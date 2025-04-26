dbt project!

### Using the starter project

Use the following queries in Snowflake to setup.
-- create accounts
use role accountadmin;

create warehouse dbt_wh with warehouse_size='x-small';
create database if not exists dbt_db;
create role if not exists dbt_role;

show grants on warehouse dbt_wh;

grant role dbt_role to user jayzern;
grant usage on warehouse dbt_wh to role dbt_role;
grant all on database dbt_db to role dbt_role;

use role dbt_role;

create schema if not exists dbt_db.dbt_schema;

-- clean up
use role accountadmin;

drop warehouse if exists dbt_wh;
drop database if exists dbt_db;
drop role if exists dbt_role;

Once the account is set up, you need to connect snowflake to the dbt.
use following commands-(You should have your python installed already)
    pip install dbt-snowflake
    pip install dbt-core

Run the following command to set up the dbt project
    dbt init
Enter the credentials as per your snowflake account and the locater(you can find it in snowflake>account>locater)

Then boom, start building your own models(SQL files) which can be views or tables (You can configure them in project.yml file)

Try running the following commands:
- dbt run
- dbt test


### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](https://community.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
