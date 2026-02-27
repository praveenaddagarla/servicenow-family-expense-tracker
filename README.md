# 💰 Family Expense Tracker using ServiceNow

## 📌 Project Overview
This project is a custom ServiceNow application developed to automate and simplify daily family expense tracking.  
Users can log daily expenses, and the system automatically updates a master Family Expenses table using a Business Rule.

This project demonstrates ServiceNow application development including custom tables, scripting, knowledge articles, and update set management.

---

## 🛠 Platform
ServiceNow – Global Application

---

## 🎯 Project Objectives
• Record daily expenses easily  
• Automatically calculate total family expenses by date  
• Maintain centralized expense records  
• Demonstrate ServiceNow development skills  

---

## 🧩 Application Components

### 🔹 Custom Tables Created
1. **Daily Expenses (u_daily_expenses)**
   - Family Member Name  
   - Date  
   - Expense Amount  
   - Comments  

2. **Family Expenses (u_family_expenses)**
   - Date  
   - Total Amount  
   - Expense Details (Auto updated)

---

## ⚙️ Automation Logic (Business Rule)

Whenever a Daily Expense record is created, a Business Rule:
- Checks if record exists for the same date
- Adds new expense to total amount
- Updates expense details automatically

### Business Rule Script

```javascript
(function executeRule(current, previous) {

var FamilyExpenses = new GlideRecord('u_family_expenses');
FamilyExpenses.addQuery('u_date',current.u_date);
FamilyExpenses.query();

if(FamilyExpenses.next())
{
    FamilyExpenses.u_amount += current.u_expense;
    FamilyExpenses.u_expense_details += ">" + current.u_comments + ":" + "Rs." + current.u_expense + "/-";
    FamilyExpenses.update();
}
else
{
    var NewFamilyExpenses = new GlideRecord('u_family_expenses');
    NewFamilyExpenses.u_date = current.u_date;
    NewFamilyExpenses.u_amount = current.u_expense;
    NewFamilyExpenses.u_expense_details += ">" + current.u_comments + ":" + "Rs." + current.u_expense + "/-";
    NewFamilyExpenses.insert();
}

})(current, previous);
```

## 📚 Knowledge Base Articles
• Workstation Security Standard  
• Phishing Awareness  
• Technical Setup Guide  

---

## 📸 Screenshots
Screenshots of the working application are available in the **screenshots** folder.

---

## 📦 Repository Contents
• ServiceNow Update Set XML  
• Project Report PDF  
• Application Screenshots  
• README Documentation  

---

## 🎥 Project Demo Video
Watch the working demo here:
https://drive.google.com/file/d/1eTQ0_Kob5ol3Ychd3dSv-RDfzg1Oioto/view?usp=sharing

---

## 👨‍💻 Developer
**Addagarla S S R Praveen**  
APSHE Smartz Internship – 2026
