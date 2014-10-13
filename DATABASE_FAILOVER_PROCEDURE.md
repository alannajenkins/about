### RDS Failover Proceedure

If we have unrecoverable database issues then the only way to get a database back up and running is to build a new instance from scratch using the following proceedure.

1. Log in to the "AWS Management Console" and got to the "RDS" screen.  
2. From the "RDS Dashboard" on the left hand side choose "Instances" and you will see the list of RDS instances we have running.
3. Right-click on the RDS you wish to create a new version of and choose "Restore to Point In Time".  This will take you to the "Restore DB Instance" page.
4. At the top of the restore page, "Use Latest Restorable Time" will be selected by default and will tell you how recent the restore is up to.  Most fields will be set up already to replicate the original hardware settings, you will need to  fill in DB Instance Identifier (a name for the RDS), it should be something relevant, probably similar to the name of the instance you are copying.
    
5. Click "Launch DB Instance", this will begin the creation of the database and associated infrastructure.  Depending on the storage type chosen and the amount of data in the tables, this can take anywhere from 10 minutes to hours.

6. Once the database is accessible you can tell from the status on the "Instances" screen, grab the host name (Endpoint without the port number and comma) and go to Route53.
7. Select the name of the service you need to change (if you are rebuilding the shortbreaksrds it will be rds-production.t-bob.co.uk).
8. On the right hand side you will see the CName editor, for the value textbox replace the contents with your new host and click "Save Record Set".  If will take up to 5 minutes to propagate the changes.
9. Sit back and relax, the panic has been mitigated.
