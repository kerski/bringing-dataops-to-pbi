# Conducting Tests using Sample Model.

These instructions are a continuation from <a href="https://www.kerski.tech/bringing-dataops-to-power-bi-part4/" target="_blank">Part 4 of Bringing DataOps to Power BI</a>.  The steps below describe how to setup the "Sample Model.pbit" file to run tests within DAX Studio.

## Prerequisites

-   Power BI Desktop installed on device executing these steps.

-   <a href="https://daxstudio.org/">DAX Studio</a> installed

## Steps
1. Download or clone the current repository to your device.  Open the file labeled "SampleModel.pbit".

![File explorer with SampleModel.pbit](./images/Figure0.png)

2. Once Power BI Desktop opens you should be prompted to enter a URL in the WebURL field.  Enter "https://raw.githubusercontent.com/fivethirtyeight/data/master/comic-characters/marvel-wikia-data.csv" and press the "Load" button.
![SampleModel prompt](./images/Figure1.png)

3. The Power BI file should attempt to load the data into the model. As long as you have Internet access, this step should take a few minutes to complete.
![Refresh example](./images/Figure2.png)

4. Open DAX Studio and you will be presented with a prompt titled "Connect". Select the "PBI / SSDT Model" radio button and select the model labeled "Untitled".

![DAX Studio Connect](./images/Figure3.png)

5. In the top left corner of DAX Studio select the File->Open->Browse option and navigate to where you downloaded or cloned the files from step 1.

![DAX Studio File Open example](./images/Figure4a.png)

6. Select the "TableTests.msdax" file and a new tab with the file contents should open. Each test file consistents of three areas:

- **Setup** (Lines 3-11): This is where you define the filters and DAX measures for testing.
- **Execution** (Lines 13-31): This is where you define a variable called "_Tests" that unions each test.  Each test is encapsulated by a Row defintion consisting of the columns Test name, Expected Value, and Actual Value.
- **Output** (Lines 33-34): This takes the results of the "_Tests" variable and evaluates each row's Expected and Actual value to verify that they match.  The result is a boolen outputed in a new column called "Passed"

![Measure Tests example](./images/Figure4.png)

7. Select the run button and the tests should execute and display the results.

![Refresh example](./images/Figure5.png)