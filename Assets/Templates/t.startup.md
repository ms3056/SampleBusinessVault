<%*
async function createIfNotExists(tp, filepath){ 
    if (!(await tp.file.exists(filepath))){ 
        app.fileManager.createAndOpenMarkdownFile(filepath) 
    } 
} 

let now = moment();  // Create a moment object for the current date/time

// Capture the quarter value at this point
let currentQuarter = now.quarter();

// Daily Note Creation
let dailyYear = now.year();  // Get the current year
let dailyMonth = (now.month() + 1).toString().padStart(2, '0');  // Get the current month (1-based), padded with '0' to 2 digits
let dailyDay = now.date().toString().padStart(2, '0');  // Get the current day, padded with '0' to 2 digits
let dailyNotePath = "Journal/Daily/" + dailyYear + "-" + dailyMonth;
let dailyNoteName = dailyYear + "-" + dailyMonth + "-" + dailyDay + ".md";

await createIfNotExists(tp, dailyNotePath + "/" + dailyNoteName);

// Weekly Note Creation
let startOfWeek = now.startOf('week');  // Get the start of the week
let weekStartYear = startOfWeek.year();  // Get the year of the start of the week

// Correcting the year for the week start if it falls in the previous year
if (weekStartYear < dailyYear) {
    weekStartYear = dailyYear;
}

let weekStartWeek = "W" + startOfWeek.week().toString().padStart(2, '0');  // Get the week number of the start of the week, prefixed with 'W', with leading zero
let weeklyNotePath = "Journal/Weekly/" + weekStartYear + "-" + dailyMonth;  // Using dailyMonth for the path
let weeklyNoteName = weekStartYear + "-" + weekStartWeek + ".md";

await createIfNotExists(tp, weeklyNotePath + "/" + weeklyNoteName);

// Quarterly Note Creation with leading zero in quarter
let quarter = "Q" + currentQuarter;  // Use the captured quarter value
let quarterlyNotePath = "Journal/Quarterly/" + dailyYear;  // Path with the current year
let quarterlyNoteName = dailyYear + "-" + quarter + ".md";
await createIfNotExists(tp, quarterlyNotePath + "/" + quarterlyNoteName);

// Yearly Note Creation
await createIfNotExists(tp, "Journal/Yearly/" + tp.date.now("YYYY") + ".md");

%>
