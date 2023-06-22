# mv snowflake-jdbc-3.13.8.jar $GITHUB_WORKSPACE/



SNOWFLAKE_ACCOUNT: ${{ secrets.SF_ACCOUNT }}
          SNOWFLAKE_USER: ${{ secrets.SF_USERNAME }}
          SNOWFLAKE_PASSWORD: ${{ secrets.SF_PASSWORD }}
          SNOWFLAKE_DATABASE: ${{ secrets.SF_DATABASE }}
          SNOWFLAKE_SCHEMA: ${{ secrets.SF_SCHEMA }}
          SNOWFLAKE_ROLE: ${{ secrets.SF_ROLE }}


liquibase --defaultSchemaName ${{ secrets.SF_SCHEMA }} --defaultsFile liquibase.properties --username ${{ secrets.SF_USERNAME }} --password ${{ secrets.SF_PASSWORD }} --url jdbc:snowflake://${{ secrets.SF_ACCOUNT }}.snowflakecomputing.com/?db=${{ secrets.SF_DATABASE }} --classpath $GITHUB_WORKSPACE/snow-driver/snowflake-jdbc-3.13.8.jar --changeLogFile $GITHUB_WORKSPACE/changesets/....sql tag ${{ github.job }}



liquibase --defaultSchemaName RAWSTAGE --defaultsFile liquibase.properties --username gauravt --password GYT1102Rekha --url jdbc:snowflake://sqspfbf-indigochart_partner.snowflakecomputing.com/?db=RAW --classpath snowflake-jdbc-3.13.27.jar --changeLogFile changelog-ABCD1234-0.0.1.sql update
