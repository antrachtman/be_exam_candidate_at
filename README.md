# SCOIR Technical Interview for Back-End Engineers
This repo contains an exercise intended for Back-End Engineers.

## Instructions
1. Fork this repo.
1. Using technology of your choice, complete [the assignment](./Assignment.md).
1. Update this README with
    * a `How-To` section containing any instructions needed to execute your program.
    * an `Assumptions` section containing documentation on any assumptions made while interpreting the requirements.
1. Before the deadline, submit a pull request with your solution.

## Expectations
1. Please take no more than 8 hours to work on this exercise. Complete as much as possible and then submit your solution.
1. This exercise is meant to showcase how you work. With consideration to the time limit, do your best to treat it like a production system.


=========HOW TO=========
1) Install the JDK (http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
2) Install Netbeans (Only tested with V8.2 on Windows 7 x64 bit).
3) Using netbeans supporting Java SE (https://netbeans.org/downloads/)
	If you do not have the Apache Commons IO 2.5 library, you will need it. (http://commons.apache.org/proper/commons-io/download_io.cgi)
	An alternate solution is to just use the files I have included. (commons-io-2.5.jar and commons-io-2.5-javadoc.jar)

4) Download and unzip "Csv to JSON file converter.zip"
	Unzip using something like 7zip (http://www.7-zip.org/download.html)

5) Unzip SeedExamFinal(v4.0).zip from the zips folder or use the already unzipped SeedExamFinal(v4.0).

6) Open the Netbeans IDE

7) In the top lefthand corner menu go to 
	File > Open Project

8) Navigate to the unzipped SeedExamFinal(v4.0) and double click on it to open the project
	At this point, you may get an error that says "Project Problems - One or more project resources could not be found"
	If this is the case then take the commons-io-2.5.jar and commons-io-2.5-javadoc.jar files and note their location.
	Go to the projects tab (ctrl + 1) and right click on Libraries
	Click on Add JAR/Folder
	Select commons-io-2.5.jar and commons-io-2.5-javadoc.jar
	This should resolve the error.

9) Click the green arrow under the top toolbar to run the program (It's next to the hammer and broom)
	Alternatively, hit F6.

10) Let the program run. It will start up and create directories as defaults. The data directory is not cuztomizable, but the others are.

11) If you wish to change the directories, go to the unzipped folder SeedExamFinal(v4.0) and double click the data folder.

12) Open directories.txt with your favorite text editor (tested with notepad and notepad++)

13) The standard directories are for inputs, outputs and errors in that order exactly.
	Modify the directories that will be used. Example:
	C:/Users/Me/Desktop/SomeFolder/IWantThisAsMyInputDirectory
	C:/Users/Me/Desktop/ANewFolder/AnotherFolder/IWantThisAsMyOutputDirectory
	C:/Users/Me/Desktop/IWantThisAsMyErrorDirectory

	So, the first line of the file corresponds to the input directory pathing.
	The second line corresponds to output.
	The third line corresponds to error logging.
	
	Do not modify data.txt since it keeps track of previously modified files. You can clear this if you wish to reprocess any files.

	<!--If you want to "reset" all program data, just delete the input, output, error and data files contained in SeedExamFinal(v4.0)-->


14) Create a .csv file. (Tested by taking a .txt and changing the extension. Modified in notepad)
	!Do not create the file in the input folder, it will likely get deleted immediately.
	!As long as the .csv is a plain old .csv, you can create the file in excel too. Keep the special "extra features" off

15) Ensure the .csv file follows this format:
	INTERNAL_ID,FIRST_NAME,MIDDLE_NAME,LAST_NAME,PHONE_NUM
	1,data2,data3,data4,111-111-1111
	2,data5,data6,data7,123-123-1231
	3,data9,data10,data11,333-333-3333
	
	I have included some .csv files for use if desired or as examples. They are located in the Example CSVs folder.

	Do not use spaces between any inputs. At the present time, if any commas are present in the data such as:
	
	123,John,Carlson,"Smitthy, the Brave",123-123-1233
	
	The program will chug along. It won't crash, but it will generate an error log and the file will not output.
	Since headers were guaranteed, the program doesn't actually check them.

16) Take the .csv you created and place it into the inputs directory folder (whatever folder you've specified or the default.)

17) The file will process and delete itself.
	The .json file will output to the output directory if no errors were encountered. Otherwise nothing will be generated
	The error file will output to the error directory if there were any errors encountered. Otherwise nothing will be here.
	The data file will be updated with the names of the file(s) processed. You can dump multiple files into input at once.

18) When finished, go into Netbeans and check the very bottom of the window. There should be a bar with "running..." next to SeedExam (run)
    Click the [x] to the right of that bar to stop the program.
	
=========Assumptions=========
- I assumed that the directories are folders that contain files.
- I assumed that the input file is to be monitored at all times once the program starts.
- I assumed that once a file has been processed, it should be added to the list of previously input files only if it was a .csv (So for example, test.txt would not be recorded as having been seen before.)

- Because all csv files will have headers according to the instructions I skipped validating them. Especially since the headers don't follow the validation rules (the ID and the phone_num)
- On top of that, I assumed that the headers will NOT be converted into json.
- I assumed that we would only ever have names and entires that do not contain stray commas. Although it is indeed possible that it could happen in reality. I didn't implement this due to time constraints.

- I assumed that the error file names were to be exactly the same as the input file, so the error files will still come out as .csv.
- I assumed that if an error was found, the .csv should not be converted into a .json file because then the json object would contain error codes or incorrect inputs.
- I assumed that no one would have an ID, name or phone number that looks like +++ERROR01+++. However, I'm sure someone clever could figure it out and mess with it.
- I assumed that 'characters' included symbols excluding comas.

- I assumed that the user would not be changing directories on the fly and would not be deleting directories while the program is running.
- I assumed that requiring an IDE to run this would be ok due to the nature of the project.
- I assumed that the json formatting would just be sequential. Ex:

   {
       id: <INTERNAL_ID>,
       name: {
           first: "<FIRST_NAME>",
           middle: "<MIDDLE_NAME>", // omitted if blank
           last: "<LAST_NAME>"
       },
       phone: "<PHONE_NUM>"
   }
   {
       id: <INTERNAL_ID>,
       name: {
           first: "<FIRST_NAME>",
           middle: "<MIDDLE_NAME>", // omitted if blank
           last: "<LAST_NAME>"
       },
       phone: "<PHONE_NUM>"
   }
   {
       id: <INTERNAL_ID>,
       name: {
           first: "<FIRST_NAME>",
           middle: "<MIDDLE_NAME>", // omitted if blank
           last: "<LAST_NAME>"
       },
       phone: "<PHONE_NUM>"
   }
   {
       id: <INTERNAL_ID>,
       name: {
           first: "<FIRST_NAME>",
           middle: "<MIDDLE_NAME>", // omitted if blank
           last: "<LAST_NAME>"
       },
       phone: "<PHONE_NUM>"
   }

- I did assume that the user would be running Windows 7 x64
- I assumed that the user would not be changing the directories to be referenced while the program was running.
	It won't cause an error, but it also won't work. Changes will take effect the next time the program is run.
	Until the program is run again, it will continue to work on the same input/output/error directories.

- I assumed that the user would not modify the location of the data directory.