#  REST API Jmeter Runner


Currently test is set-up to run against Staging environment and company xmapi-auto.
In order to run against different environment please update variables in jmeter.properties 


Following data set-up is required to run mobile-api-jmeter test:

1. Create a role with 'View Person' permission checkbox check within this role.

2. Remove 'View Alerts' and 'View Own Events' from 'Standard User' role.

3. Import attached 'Major Incident Notification Suite' Engine in company under test.

4. Enable Engine/Form, enable form as web service enabled. 

5. Provide muser and suser(created below) permisiion to initiate BCM Engine.

6. Provide canderson(created below) permisiion to form and scenarios.



Create the following users with following below details:

7. UserID:muser, firstName:mobile, lastName:user, Role: Full Access User

8. UserID:suser, firstName:standard, lastName:user, Role: Standard User

9. UserID:jbuttler, firstName:Jos, lastName:Buttler, Role: ViewPerson, Devices:Email(Home Email) TimeZone: Asia/Calcutta

10. UserID:canderson,firstName:Corey,lastName:Anderson,Site:Default Site,Language:English,TimeZone:US/Eastern,Role:View Person role created above

11. Devices:Email(Home Email), FAX(Fax), TEXT_PHONE(SMS_Phone), TEXT_PAGER(Pager), VOICE(Mobile Phone)

12. UserID: !@#$%^&*;':",.?,firstName:special,lastName:character,Site:Default Site,Language:English,TimeZone:US/Pacific,Role:View Person role created above

13. Create user 'auser' with email device

14. create a group 'Mobile-API-Group' with users (muser, suser, jbuttler) as recipient, with 5 min delay between each user, 24x7 shift(shift name: Custom Shift: 05:00AM to 10:30PM).

15. create a group 'mobile-api' with 24x7 shift, user 'suser' added as a recipient.

16. create a DT 'UserDT'with 'auser' as a recipient.

17. Replace jbuttler with canderson

To run functional test:
```./gradlew functionalTest jmeterRun```

To open JMeter Edit mode:
```./gradlew addToJmeterClasspath jmeterEditor```

To clean Reports

'gradle jmeterCleanReport' cleans up the jmeter-test folder.

'./gradlew clean'

### Stuff used to make this:

 * https://github.com/kulya/jmeter-gradle-plugin/wiki
 
 
Basic useful feature list:
 * Uses the jmeter-gradle-plugin https://github.com/kulya/jmeter-gradle-plugin/wiki to allow the running of jmeter tests automatically
 
 


