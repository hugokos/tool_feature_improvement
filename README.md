# Project Title

The lending software that was built so far has been a big success for the company and bizops has requested that the software prompt the user to save the qualifying loans as a new CSV file.

---

## Technologies

Project uses:
["Fire"](https://github.com/google/python-fire)

["Questionary"](https://questionary.readthedocs.io/en/stable/index.html)

---

## Installation Guide

Run this program in terminal and have a folder destination for CSV exports.



---

## Usage

Utilize command line interface (CLI) to interact with the software program

!["Command Line Interface (CLI) Example"](https://initialcommit.com/img/initialcommit/how-to-paste-in-git-bash.png)

**Key example code for CSV Export:**
```
    answer = questionary.confirm("Would you like to save your qualifying loans as a .csv file?").ask()
    if answer:
        csvpath = questionary.text("Enter a file path to where you would like your file saved:").ask()
        csvpath = Path(csvpath)
        if not csvpath.exists():
            sys.exit(f"Oops! Can't find this path: {csvpath}")

        # Set the output header
        header = ["bank_data", "credit_score", "debt", "income", "loan_amount", "home_value"]

        # Create a Path to a new CSV file
        csvpath = Path("qualifying_loans.csv")

        print("Writing the data to a CSV file...")

        # Open the output CSV file path using `with open`
        with open(csvpath, "w") as csvfile:
            # Create a csvwriter
            csvwriter = csv.writer(csvfile, delimiter=",")

            # Write the header to the CSV file
            csvwriter.writerow(header)

            # Write the values of each dictionary inside of `qualifying_loans` as a row in the CSV file.
            csvwriter.writerow(qualifying_loans)
    else:
         print("Thank you")
```

---

## Contributors

Hugo Kostelni

---

## License

Open Source
