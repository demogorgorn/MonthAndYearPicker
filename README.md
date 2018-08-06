# MonthAndYearPicker

Month and Year Picker allow user to pick only month and year or only month or only year as required. You will get notified for all action's such as on selection of date, on selection of month and on section of year.

## This is a modified fork.

Original library is here - https://github.com/premkumarroyal/MonthAndYearPicker 

What's the difference?

First of all I've added following methods:

Methods | Docs
------------ | -------------
setMonthFormat(String format) |  Format for the month label in the list.
setLocale(Locale locale) |  Now there is possibility to use custom Locale. In the original version month names were in a predefined in resources array of strings (only in English). In the case you don't want to specify the locale - I've added the method to get current system locale. 
setMonthNamesArray(int arrayResId) | This one is good! You can specify id of string array in resources for month labels. If array is translated in other language - library will use it. Also the month name in header will be taken from this array.
setMonthTitleFormat(String format) | Format for the month label in the header of dialog.
setMonthSelectedCircleSize(int size) | Size of circle of selected month item (note that size is representing DP value).
setPositiveText(int resId) | Set resource string used for the positive button's text
setNegativeText(int resId) | Set resource string used for the negative button's text

And styles (examples):

    <style name="MonthPickerDialogStyle" >
        <item name="monthTextSize">12sp</item>
    </style>


What else?

Fixed layout in the header - there was an issue with centering view in header when only one mode (showYearOnly() or showMonthOnly()) was enabled.


## Sample Project output:

![MonthAndYearPicker](https://github.com/premkumarroyal/MonthAndYearPicker/blob/master/sample/src/main/res/raw/datepicker.gif?raw=true "Month and Year Picker") ![MonthAndYearPicker](https://j.gifs.com/nZpE4P.gif?raw=true "Choose Month") ![MonthAndYearPicker](https://github.com/premkumarroyal/MonthAndYearPicker/blob/master/sample/src/main/res/raw/choose_year.gif?raw=true "Choose Year") ![MonthAndYearPicker](https://j.gifs.com/LgoKEv.gif?raw=true "Choose Quantity")


# Code

     MonthPickerDialog.Builder builder = new MonthPickerDialog.Builder(MainActivity.this, 
     new MonthPickerDialog.OnDateSetListener() {
       @Override
       public void onDateSet(int selectedMonth, int selectedYear) { // on date set }
     }, today.get(Calendar.YEAR), today.get(Calendar.MONTH));
    
    builder.setActivatedMonth(Calendar.JULY)
           .setMinYear(1990)
           .setActivatedYear(2017)
           .setMaxYear(2030)
           .setMinMonth(Calendar.FEBRUARY)
           .setTitle("Select trading month")
           .setMonthRange(Calendar.FEBRUARY, Calendar.NOVEMBER)
           // .setMaxMonth(Calendar.OCTOBER)
           // .setYearRange(1890, 1890)
           // .setMonthAndYearRange(Calendar.FEBRUARY, Calendar.OCTOBER, 1890, 1890)
           //.showMonthOnly()
           // .showYearOnly()
           .setOnMonthChangedListener(new MonthPickerDialog.OnMonthChangedListener() {
             @Override
             public void onMonthChanged(int selectedMonth) { // on month selected } })
           .setOnYearChangedListener(new MonthPickerDialog.OnYearChangedListener() {
              @Override
              public void onYearChanged(int selectedYear) { // on year selected } })
            .build()
            .show();
                        
## Listeners
    setOnMonthChangedListener(OnMonthChangedListener());
    setOnYearChangedListener(OnYearChangedListener());

## Methods
 Methods | Docs
------------ | -------------
setMaxMonth(int maxMonth) |  Maximum month that user can select.
setMinMonth(int minMonth) |  Minimum month that user can select.
setMonthRange(int minMonth, int maxMonth) | set both max and min sections.
setActivatedMonth(activatedMonth) | selected the month when picker opens.
setMaxYear(int maxYear) | Maximum year that will be shown in picker.
setMinYear(int minYear) | Minimum year that will be shown in picker.
setYearRange(int minYear, int maxYear) | set both max and min selections.
setActivatedYear(activatedYear) | selected the year when picker opens.
setMonthAndYearRange(int minMonth, int maxMonth, int minYear, int maxYear) | set month and year min and max values at once.
showMonthOnly() | Only month selection will be shown.
showYearOnly() | Only year selection will be shown.
setTitle(String title) | set the title for Month Picker Dialog. By default title will be hidden, it will be visible if value set.
setOnMonthChangedListener(MonthPickerDialog.OnMonthChangedListener onMonthChange); | Listener for select month
setOnYearChangedListener(MonthPickerDialog.OnYearChangedListener onYearChange); | Listener for year select year


## Styling

Month and Year picker by default pick the color from theme if you declared colorAccent. If you want to change color's you can override the theme as below.

     <style name="MonthPickerDialogStyle" >
        <item name="monthBgColor">@color/bgColor</item>
        <item name="monthBgSelectedColor">@color/colorAccent</item>
        <item name="monthFontColorSelected">@color/selectionColor</item>
        <item name="monthFontColorNormal">@color/bgColor</item>
        <item name="monthFontColorDisabled">@color/bgColor</item>

        <item name="headerBgColor">@color/colorAccent</item>
        <item name="headerFontColorSelected">#fff</item>
        <item name="headerFontColorNormal">#85FFFFFF</item>
        <item name="headerTitleColor">#fff</item>

        <item name="dialogActionButtonColor">@color/colorAccent</item>
    </style>


## Usage 

Step 1. Add it in your root build.gradle at the end of repositories:

    allprojects {
        repositories {
          ...
          maven { url 'https://jitpack.io' }
        }
    }

Step 2. Add the dependency

    dependencies {
        implementation 'com.github.demogorgorn:MonthAndYearPicker:1.0.11'
    }

or Maven

Step 1. Add the JitPack repository to your build file


    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>

Step 2. Add the dependency

    <dependency>
        <groupId>com.github.demogorgorn</groupId>
        <artifactId>MonthAndYearPicker</artifactId>
        <version>1.0.11</version>
    </dependency>
   




