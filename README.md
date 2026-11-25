# Address Book Management System (C)

A console-based Address Book application written in C. It lets you create, search, edit, delete and list contacts, and saves everything to a CSV file so your data is still there the next time you run it. Input is validated, and phone numbers and emails are kept unique.

Developed as part of the Advanced Embedded Systems program at Emertxe.

## Features

- **Menu-driven interface** that keeps running until you choose Exit
- **Create** a contact with name, phone number and email
- **Search** a contact by name, phone number or email
- **Edit** the name, phone number or email of an existing contact, chosen by its serial number
- **Delete** a contact, with a (y/n) confirmation before removing it
- **List** all contacts in a neat table with serial numbers
- **Input validation** for name, phone and email, asking again until the input is valid
- **Duplicate check** so no two contacts share a phone number or an email
- **Automatic lowercase** conversion of email addresses
- **Persistent storage** in `contact.csv`: loaded at start-up and saved on exit
- **Safe handling** of a full address book (100 contacts), a missing CSV file and invalid menu choices

## Input Validation

| Field | Rules |
|-------|-------|
| Name | Letters and spaces only |
| Phone | Exactly 10 digits, starts with 6, 7, 8 or 9, must be unique |
| Email | Converted to lowercase, only letters, digits, `@` and `.` allowed, exactly one `@` (not at the start), must end with `.com`, must be unique |

The same rules apply when editing a contact. Duplicate phone numbers and emails are rejected.

## Project Structure

```
ADDRESS_BOOK/
├── main.c         # Menu loop and program entry point
├── contact.c      # Create, search, edit, delete, list, load/save and validation logic
├── contact.h      # Structures, MAX_CONTACTS and function declarations
├── populate.c     # initialize() function (loads contacts from the CSV file)
└── contact.csv    # Saved contacts (name,phone,email)
```

## How to Compile and Run

```bash
gcc main.c contact.c populate.c -o addressbook
./addressbook
```

## Menu

```
Address Book Menu:
1. Create contact
2. Search contact
3. Edit contact
4. Delete contact
5. List all contacts
6. Exit
Enter your choice:
```

Choose **6** to save your contacts to `contact.csv` and exit. Contacts are only written to the file when you exit through this option.

## CSV File Format

Each line holds one contact as `name,phone,email`:

```
Asha Rao,9876543210,asha@gmail.com
Ravi Kumar,9123456780,ravi@gmail.com
```

## Concepts Used

- Structures and arrays
- Modular programming with multiple source files and a header file
- File handling (`fopen`, `fscanf`, `fprintf`, `fclose`)
- String handling (`strcpy`, `strcmp`, `strchr`) and character checks (`isalpha`, `isdigit`, `islower`)
- Input validation with loops

## Possible Improvements

- Partial and case-insensitive search
- Sorting contacts by name
- Dynamic memory allocation instead of a fixed 100-contact limit

## Author

Pravallika Talari
B.Tech ECE-Kuppam Engineering College (2026)
Advanced Embedded Systems Training--Emertxe Information Techonologies,Bengaluru
GitHub:github.com/pravali18
Linkedin:linkedin.com/in/talari-pravallika1830

