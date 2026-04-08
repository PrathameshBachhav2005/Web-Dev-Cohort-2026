# Clinic Appointment and Diagnostics Platform
```  1. Show all patients
SELECT * FROM Patient;

 2. Show all doctors
SELECT * FROM Doctor;

3. List all appointments with patient and doctor names (Very Useful)
SELECT 
    a.appointment_id,
    p.name AS patient_name,
    d.name AS doctor_name,
    a.appointment_date,
    a.appointment_time,
    a.status
FROM Appointment a
JOIN Patient p ON a.patient_id = p.patient_id
JOIN Doctor d ON a.doctor_id = d.doctor_id
ORDER BY a.appointment_date DESC; ```



``` 4. Today's Appointments
SELECT 
    a.appointment_id,
    p.name AS patient_name,
    d.name AS doctor_name,
    a.appointment_time,
    a.status
FROM Appointment a
JOIN Patient p ON a.patient_id = p.patient_id
JOIN Doctor d ON a.doctor_id = d.doctor_id
WHERE a.appointment_date = CURDATE()
ORDER BY a.appointment_time;
 ```


```   
 5. Show Consultations with Diagnosis
SELECT 
    c.consultation_id,
    p.name AS patient_name,
    d.name AS doctor_name,
    c.consultation_date,
    c.diagnosis_notes
FROM Consultation c
JOIN Patient p ON c.patient_id = p.patient_id
JOIN Doctor d ON c.doctor_id = d.doctor_id
ORDER BY c.consultation_date DESC;
```