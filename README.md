# FishbowlDataExtractor
This is Fishbowl Data Extractor windows service

This service checks for daily generated CSV files/reports from Fishbowl. It can send the day's new file or send deltas between todays file and yesterdays file. 

To use this service, run this installer and follow the prompts.

To configure the service, make sure the service is stopped and edit the FishbowlDataExtractor.exe.config file located in your chosen installation directory.


Standard config will look like this. Comments above each line explain the variables.

  <appSettings>
    <!-- How long between service runs, default is 24 hours -->
    <add key="TimerInterval" value="86400000"/>
    <!-- Hour of the day to run, in 24 hour intervals -->
    <add key="HourToRun" value="23"/>
    <!-- Minute of that hour to run -->
    <add key="MinuteToRun" value="10"/>
    <!-- Overall directory to check for files. Specific directories and their recipients are listed in the RegisterCustomConfig section -->
    <add key="DirectoryToCheck" value="C:\Program Files\Fishbowl\DataExports"/>
    <!-- Basic email settings -->
    <add key="EmailClientHost" value="801425-exch01"/>
    <add key="EmailClientTimeout" value="10000"/>
    <add key="EmailClientUsername" value="example@example.com"/>
    <add key="EmailClientPassword" value=""/>
    <add key="EmailFrom" value="exampe@example.com"/>
    <add key="EmailSubject" value="Fishbowl Data Export - {0}"/>
    <add key="EmailBody" value="Attached is a Fishbowl data export for today."/>
  </appSettings>

  <RegisterCustomConfig>
    <Directories>
      <!-- Name of a directory to check, who should get the emails, and if only deltas between the day's files should be sent -->
      <Directory name="Example" recipients="example1@example.com|example2@example.com" onlysendcsvdeltas="true"/>
   </Directories>
  </RegisterCustomConfig>


Copyright 2017 Black Hall Digital
