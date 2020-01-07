# ETL Documentation

##     ETL Summary
* There are 14 ETL syncs which would be scheduled using a cron named __sync-all-icici-data__.

* An Entry will be created in __cron_log__ table  
    * __cron_job_name__ will be **sync-all-icici-data**
    * __cron_status__
        * 2: Error In Cron
        * 3: Finished Successfully
    * __log__ will show any error in the cron
    * __start_date__ shows start date of Cron job
    * __end_date__ shows end date of Cron job 
     
* An Entry will be created in __data_sync_log__ table for each ETL sync which shows the summary of ETL job
    * __source_name__ will be **ICICI** in all cases 
    * __task_name__ shows the ETL Name
    * __record_count__ shows the number of record in source table
    * __success_count__ shows the distict number of records succeded  
    * __failue_count__ shows the distict number of records failed
        * Each failed record will have an entry in __etl_error_log__ with the failed record and reason in __error_message__ column
    * __status__ will be 0 in case of ```failue_count > 0 ``` else it will be ```1```
    * __start_date__ shows start date of ETL job
    * __end_date__ shows end date of ETL job

## Manually Running a ETL Job

For running an ETL manually enter in the console mode using 
```
node . --console
```
then run any ETL from the list shown below - 
```javascript
app.engines.IciciSyncForFamily.syncFamilyData()
app.engines.IciciSyncForClient.syncClientData()
app.engines.IciciSyncForInvestorDetails.syncInvestorDetailsData()
app.engines.IciciSyncForAccount.syncAccountData()
app.engines.IciciSyncForInstrument.syncInstrumentData()
app.engines.IciciSyncForTransaction.syncTransactionData()
app.engines.IciciSyncForHolding.syncHoldingData()
app.engines.IciciSyncForRmDetails.syncRelationshipManagerDetailsData()
app.engines.IciciSyncForRmClientEntityMapping.syncRmClientEntityMapping()
app.engines.IciciSyncForLoan.syncLoanDeails()
app.engines.IciciSyncForInsurance.syncInsuranceDeails()
app.engines.IciciSyncForCreditCard.syncCreditCardDeails()
app.engines.IciciSyncForBankBalance.syncBankBalanceDeails()
app.engines.IciciSyncForDeposit.syncDepositDeails()
```
