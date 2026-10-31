const prompt = require("prompt-sync")();

console.log("!!!=> WELCOME TO LAGBAJA SCHOOL RECORDS <=!!!");
console.log("_=_=> WHICH GRADE'S RECORD DO YOU WISH TO CREATE: <=_=_");
let grade = Number(prompt(""));

console.log("Number of students please: ");
let numberOfStudents = Number(prompt(""));
console.log("Saved--->");

console.log("Number of subjects taken please");
let numberOfSubjects = Number(prompt(""));
console.log("Saved--->");

console.log("_=_=> CREATING GRADE " + grade + " RECORDS SHEET <=_=_");

let recordBook = [];
for (let index = 0; index < numberOfStudents; index++) {
    let row = [];
    for (let spot = 0; spot < numberOfSubjects + 3; spot++) {
        row.push(0);
    }
    recordBook.push(row);
}

for (let index = 0; index < numberOfStudents; index++) {
    console.log("NEW STUDENT: STUDENT " + (index + 1));
    for (let index_a = 0; index_a < numberOfSubjects; index_a++) {
        console.log("ENTER STUDENTS SUBJECT SCORE");
        let score = Number(prompt(""));
        while (score < 0 || score > 100) {
            console.log("invalid score");
            console.log("ENTER STUDENTS SUBJECT SCORE");
            score = Number(prompt(""));
        }
        recordBook[index][index_a] = score;
    }
}

for (let index = 0; index < numberOfStudents; index++) {
    let total = 0;
    for (let index_a = 0; index_a < numberOfSubjects; index_a++) {
        total += recordBook[index][index_a];
    }
    recordBook[index][numberOfSubjects] = total;
}

for (let index = 0; index < numberOfStudents; index++) {
    let position = 1;
    for (let index_a = 0; index_a < numberOfStudents; index_a++) {
        if (recordBook[index_a][numberOfSubjects] > recordBook[index][numberOfSubjects]) {
            position += 1;
        }
    }
    recordBook[index][numberOfSubjects + 2] = position;
}

console.log("=======================================================================");
let headerLine = "Class" + grade + "|";
for (let index = 1; index < numberOfSubjects + 1; index++) {
    headerLine += " \t subject" + index + " \t ";
}
headerLine += " \t TOT \t AVE \t POS";
console.log(headerLine);
console.log("=======================================================================");

for (let index = 0; index < numberOfStudents; index++) {
    let average = recordBook[index][numberOfSubjects] / numberOfSubjects;
    let cents = average * 100 + 0.5;
    cents = cents - (cents % 1);
    let decimals = cents % 100;
    let whole = (cents - decimals) / 100;
    let decimalText = "" + decimals;
    if (decimals < 10) {
        decimalText = "0" + decimals;
    }
    let averageText = whole + "." + decimalText;
    let studentLine = "Student " + (index + 1) + " |";
    for (let index_a = 0; index_a < numberOfSubjects; index_a++) {
        studentLine += " \t " + recordBook[index][index_a] + " \t ";
    }
    studentLine += " \t " + recordBook[index][numberOfSubjects] + " \t " + averageText + " \t " + recordBook[index][numberOfSubjects + 2];
    console.log(studentLine);
}
console.log("=======================================================================");
console.log("=======================================================================");

console.log("SUBJECT SUMMARY");
let passes = [];
let fails = [];
for (let index = 0; index < numberOfSubjects; index++) {
    passes.push(0);
    fails.push(0);
}
let overallHighest = recordBook[0][0];
let overallHighestStudent = 0;
let overallHighestSubject = 0;
let overallLowest = recordBook[0][0];
let overallLowestStudent = 0;
let overallLowestSubject = 0;

for (let index_a = 0; index_a < numberOfSubjects; index_a++) {
    let highest = recordBook[0][index_a];
    let highestStudent = 0;
    let lowest = recordBook[0][index_a];
    let lowestStudent = 0;
    let subjectTotal = 0;

    for (let index = 0; index < numberOfStudents; index++) {
        let mark = recordBook[index][index_a];
        subjectTotal += mark;
        if (mark > highest) {
            highest = mark;
            highestStudent = index;
        }
        if (mark < lowest) {
            lowest = mark;
            lowestStudent = index;
        }
        if (mark >= 50) {
            passes[index_a] += 1;
        } else {
            fails[index_a] += 1;
        }
    }

    if (highest > overallHighest) {
        overallHighest = highest;
        overallHighestStudent = highestStudent;
        overallHighestSubject = index_a;
    }
    if (lowest < overallLowest) {
        overallLowest = lowest;
        overallLowestStudent = lowestStudent;
        overallLowestSubject = index_a;
    }

    let subjectCents = subjectTotal / numberOfStudents * 100 + 0.5;
    subjectCents = subjectCents - (subjectCents % 1);
    let subjectDecimals = subjectCents % 100;
    let subjectWhole = (subjectCents - subjectDecimals) / 100;
    let subjectDecimalText = "" + subjectDecimals;
    if (subjectDecimals < 10) {
        subjectDecimalText = "0" + subjectDecimals;
    }
    let subjectAverageText = subjectWhole + "." + subjectDecimalText;

    console.log("Subject " + (index_a + 1));
    console.log("Highest scoring student is: Student " + (highestStudent + 1) + " scoring " + highest);
    console.log("Lowest scoring student is: Student " + (lowestStudent + 1) + " scoring " + lowest);
    console.log("Total score is: " + subjectTotal);
    console.log("Average score is: " + subjectAverageText);
    console.log("Number of passes: " + passes[index_a]);
    console.log("Number of fails: " + fails[index_a]);
    console.log("");
}

let hardest = 0;
let easiest = 0;
for (let index_a = 1; index_a < numberOfSubjects; index_a++) {
    if (fails[index_a] > fails[hardest]) {
        hardest = index_a;
    }
    if (passes[index_a] > passes[easiest]) {
        easiest = index_a;
    }
}
console.log("The hardest subject is Subject " + (hardest + 1) + " with " + fails[hardest] + " failures");
console.log("The easiest subject is Subject " + (easiest + 1) + " with " + passes[easiest] + " passes");
console.log("The overall highest score is scored by Student " + (overallHighestStudent + 1) + " in subject " + (overallHighestSubject + 1) + " scoring " + overallHighest);
console.log("The overall lowest score is scored by Student " + (overallLowestStudent + 1) + " in subject " + (overallLowestSubject + 1) + " scoring " + overallLowest);
console.log("=======================================================================");

let bestStudent = 0;
let worstStudent = 0;
let classTotal = 0;
for (let index = 0; index < numberOfStudents; index++) {
    classTotal += recordBook[index][numberOfSubjects];
    if (recordBook[index][numberOfSubjects] > recordBook[bestStudent][numberOfSubjects]) {
        bestStudent = index;
    }
    if (recordBook[index][numberOfSubjects] < recordBook[worstStudent][numberOfSubjects]) {
        worstStudent = index;
    }
}

console.log("");
console.log("CLASS SUMMARY");
console.log("=======================================================================");
console.log("Best graduating student is: Student " + (bestStudent + 1) + " scoring " + recordBook[bestStudent][numberOfSubjects]);
console.log("=======================================================================");
console.log("");
console.log("!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!");
console.log("Worst graduating student is: Student " + (worstStudent + 1) + " scoring " + recordBook[worstStudent][numberOfSubjects]);
console.log("!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!");
console.log("");
console.log("=======================================================================");
let tenths = classTotal / numberOfStudents * 10 + 0.5;
tenths = tenths - (tenths % 1);
let tenthsDigit = tenths % 10;
let classWhole = (tenths - tenthsDigit) / 10;
let classAverageText = classWhole + "." + tenthsDigit;
console.log("Class total score is: " + classTotal);
console.log("Class average score is: " + classAverageText);
console.log("=======================================================================");
console.log("THANK YOU FOR USING OUR RECORD SYSTEM!\\(O-O)/");
