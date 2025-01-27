## **1. Introduction**  
This project is a website for doctors to manage patients and medical records. Doctors can:  
- Create an account.  
- Add/delete patients.  
- Save medical data (like medicines, allergies).  
- View patient details.  
---
## **2. Project Idea**  
**Problem:** Doctors need a simple tool to organize patient data.  
**Solution:** This website helps doctors save time and keep patient information safe.  
---
## **3. Tools Used**  
- **Frontend:** HTML, Bootstrap (for design).  
- **Backend:** Python Flask (for website logic).  
- **Database:** SQLite (stores patient data).  
---
## **4. Website Pages**  
### 4.1 Home Page  
- Shows options to login or register.  
- After login, doctors see buttons to add/view patients.  
### 4.2 Login Page  
- Doctors enter username/password.  
### 4.3 Registration Page  
- New doctors create an account.  
### 4.4 Add Patient Page  
- Form to add patient name, gender, blood type, and birth date.  
### 4.5 Patient List Page  
- Shows all patients in a table.  
### 4.6 Medical Records Page  
- Displays a patient’s medical history.  
---
## **5. Database Structure**  
### 5.1 Tables  
- **Doctors:** Stores doctor usernames and passwords.  
- **Patients:** Stores patient details (name, blood type, etc.).  
- **Medical Records:** Stores medical data (allergies, medicines).  
### 5.2 Relationships  
- One doctor ➔ Many patients.  
- One patient ➔ Many medical records.  
---
## **6. Frontend (HTML & Bootstrap)**  
- Uses Bootstrap for buttons, tables, and forms.  
- All pages use the same design (navbar, colors).  
- Example code from `base.html`:  
  ```html
  <nav class="navbar navbar-expand-lg navbar-light bg-primary">
    <a class="navbar-brand text-white" href="/">Clinical Management</a>
  </nav>
  ```  
---
## **7. Backend (Python Flask)**  
### 7.1 Features  
- Login/logout system.  
- Password encryption (safe storage).  
- Database operations (add/delete patients).  
### 7.2 Example Code from `app.py`  
```python
@app.route('/add_patient', methods=['GET', 'POST'])
def add_patient():
    form = AddPatientForm()
    if form.validate_on_submit():
        new_patient = Patient(name=form.name.data, gender=form.gender.data)
        db.session.add(new_patient)
        db.session.commit()
    return render_template('add.html', form=form)
```  
---
## **8. User Authentication**  
- Doctors must log in to see patient data.  
- Passwords are encrypted (not stored as text).  
---
## **9. Security**  
- Passwords use `werkzeug.security` library.  
- Example:  
  ```python
  hashed_password = generate_password_hash('password123')
  check_password_hash(hashed_password, 'password123')  # Returns True/False
  ```  
---
## **10. Forms**  
- Created using `Flask-WTF`.  
- Example: `AddPatientForm` includes fields for name, gender, and blood type.  
---
## **11. Error Handling**  
- Shows messages like "Invalid password" or "Patient deleted."  
- Uses Flask’s `flash()` function.  
---
## **12. Database Migrations**  
- Uses `Flask-Migrate` to update the database.  
- Example: Adding `birth_date` to the `Patient` table (file `b3c47219ce3d_added_birth_date_to_patient.py`).  
---
## **13. Testing**  
- Run the app with `app.run(debug=True)`.  
- Test by adding fake patients and records.  
---
## **14. Screenshots of Website**  
*(Add these manually in your Word document)*  
1. **Home Page**: Before and after login.  
2. **Patient List Page**: Table with sample data.  
3. **Medical Records Page**: Show allergies and medicines.  
---
## **15. Screenshots of Code**  
*(Add these manually)*  
1. **app.py**: Show routes for adding patients.  
2. **models.py**: Database table structures.  
3. **forms.py**: Registration form code.  
---
## **16. Bootstrap Components Used**  
- Navbar (blue bar at the top).  
- Buttons (green for save, red for delete).  
- Forms (styled with `form-control` class).  
---
## **17. Challenges**  
- Connecting the database to Flask.  
- Ensuring only logged-in doctors see patient data.  
---
## **18. Future Improvements**  
- Add search bar for patients.  
- Let doctors upload PDF reports.  
- Mobile-friendly design.  
---
## **19. How to Install the Project**  
1. Install Python.  
2. Run `pip install -r requirements.txt`.  
3. Run `flask run`.  
---
## **20. Conclusion**  
This project helps doctors manage patient data safely. It uses modern tools like Flask and Bootstrap. Future updates can make it even better!  
---
