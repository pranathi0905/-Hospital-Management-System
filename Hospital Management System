import Read_Hospital_Excel_Sheet
import Write_Hospital_Excel_Sheet

# Function to find appointment index in doctor's database
def AppointmentIndexInDoctorsDataBase(patient_ID, Doctors_DataBase):
    for doctor_id in Doctors_DataBase:
        for appointment in Doctors_DataBase[doctor_id]:
            if str(patient_ID) == str(appointment[0]):
                appointment_index = Doctors_DataBase[doctor_id].index(appointment)
                return appointment_index, doctor_id
    return None, None


print("****************************************************************************")
print("*                                                                          *")
print("*              Welcome Hospital Management System               *")
print("*                                                                          *")
print("****************************************************************************")

tries = 0
tries_flag = ""

while tries_flag != "Close the program":
    Pateints_DataBase = Read_Hospital_Excel_Sheet.Read_Patients_DataBase()
    Doctors_DataBase = Read_Hospital_Excel_Sheet.Read_Doctors_DataBase()

    print("-----------------------------------------")
    print("| Enter 1 for Admin mode                |")
    print("| Enter 2 for User mode                 |")
    print("-----------------------------------------")
    Admin_user_mode = input("Enter your mode: ").strip()

    # -------------------- ADMIN MODE --------------------
    if Admin_user_mode == "1":
        print("*****\n|         Welcome to Admin mode         |\n*****")
        Password = input("Please enter your password: ")

        while True:
            if Password == "1234":
                print("-----------------------------------------")
                print("| 1 - Manage Patients                   |")
                print("| 2 - Manage Doctors                    |")
                print("| 3 - Manage Appointments               |")
                print("| E - Back                              |")
                print("-----------------------------------------")
                AdminOptions = input("Enter your choice: ").upper()

                # -------------------- PATIENTS MANAGEMENT --------------------
                if AdminOptions == "1":
                    print("-----------------------------------------")
                    print("| 1 - Add New Patient                   |")
                    print("| 2 - Display Patient                   |")
                    print("| 3 - Delete Patient Data                |")
                    print("| 4 - Edit Patient Data                  |")
                    print("| B - Back                              |")
                    print("-----------------------------------------")
                    Admin_choice = input("Enter your choice: ").upper()

                    if Admin_choice == "1":
                        try:
                            patient_ID = int(input("Enter patient ID: "))
                            while patient_ID in Pateints_DataBase:
                                patient_ID = int(input("This ID is unavailable, try another: "))
                            Department = input("Enter patient department: ")
                            DoctorName = input("Enter doctor's name: ")
                            Name = input("Enter patient name: ")
                            Age = input("Enter patient age: ")
                            Gender = input("Enter patient gender: ")
                            Address = input("Enter patient address: ")
                            RoomNumber = input("Enter patient room number: ")
                            Pateints_DataBase[patient_ID] = [
                                Department, DoctorName, Name, Age, Gender, Address, RoomNumber
                            ]
                            print("✅ Patient added successfully.")
                        except ValueError:
                            print("❌ Patient ID should be an integer.")

                    elif Admin_choice == "2":
                        try:
                            patient_ID = int(input("Enter patient ID: "))
                            while patient_ID not in Pateints_DataBase:
                                patient_ID = int(input("Incorrect ID, enter again: "))
                            patient = Pateints_DataBase[patient_ID]
                            print(f"\nPatient Name: {patient[2]}")
                            print(f"Age: {patient[3]}, Gender: {patient[4]}")
                            print(f"Address: {patient[5]}, Room: {patient[6]}")
                            print(f"Department: {patient[0]}, Doctor: {patient[1]}")
                        except ValueError:
                            print("❌ Patient ID should be an integer.")

                    elif Admin_choice == "3":
                        try:
                            patient_ID = int(input("Enter patient ID: "))
                            while patient_ID not in Pateints_DataBase:
                                patient_ID = int(input("Incorrect ID, enter again: "))
                            Pateints_DataBase.pop(patient_ID)
                            print("✅ Patient deleted successfully.")
                        except ValueError:
                            print("❌ Patient ID should be an integer.")

                    elif Admin_choice == "4":
                        try:
                            patient_ID = int(input("Enter patient ID: "))
                            while patient_ID not in Pateints_DataBase:
                                patient_ID = int(input("Incorrect ID, enter again: "))
                            while True:
                                print("------------------------------------------")
                                print("| 1 - Edit Department                    |")
                                print("| 2 - Edit Doctor                        |")
                                print("| 3 - Edit Name                          |")
                                print("| 4 - Edit Age                           |")
                                print("| 5 - Edit Gender                        |")
                                print("| 6 - Edit Address                       |")
                                print("| 7 - Edit Room Number                   |")
                                print("| B - Back                               |")
                                print("------------------------------------------")
                                choice = input("Enter your choice: ").upper()
                                if choice in ["1", "2", "3", "4", "5", "6", "7"]:
                                    new_val = input("Enter new value: ")
                                    Pateints_DataBase[patient_ID][int(choice) - 1] = new_val
                                    print("✅ Patient data updated.")
                                elif choice == "B":
                                    break
                                else:
                                    print("❌ Invalid choice.")
                        except ValueError:
                            print("❌ Patient ID should be an integer.")

                    elif Admin_choice == "B":
                        continue

                # -------------------- DOCTORS MANAGEMENT --------------------
                elif AdminOptions == "2":
                    # Similar handling for Doctors (like Patients)
                    pass  # For brevity; can implement same way

                # -------------------- APPOINTMENT MANAGEMENT --------------------
                elif AdminOptions == "3":
                    # Similar handling for Appointments (like Patients)
                    pass

                elif AdminOptions == "E":
                    break
                else:
                    print("❌ Invalid option.")

                Write_Hospital_Excel_Sheet.Write_Patients_DataBase(Pateints_DataBase)
                Write_Hospital_Excel_Sheet.Write_Doctors_DataBase(Doctors_DataBase)

            else:
                if tries < 2:
                    Password = input("❌ Incorrect password, try again: ")
                    tries += 1
                else:
                    print("❌ No more tries left.")
                    tries_flag = "Close the program"
                    break

    # -------------------- USER MODE --------------------
    elif Admin_user_mode == "2":
        print("*****\n|         Welcome to User mode          |\n*****")
        while True:
            print("\n-----------------------------------------")
            print("| 1 - View Hospital Departments         |")
            print("| 2 - View Doctors                      |")
            print("| 3 - View Patients Residents           |")
            print("| 4 - View Patient Details               |")
            print("| 5 - View Doctor's Appointments        |")
            print("| B - Back                              |")
            print("-----------------------------------------")
            choice = input("Enter your choice: ").upper()

            if choice == "1":
                print("Departments:")
                for doc in Doctors_DataBase:
                    print(" - " + Doctors_DataBase[doc][0][0])
            elif choice == "2":
                print("Doctors:")
                for doc in Doctors_DataBase:
                    print(f" - {Doctors_DataBase[doc][0][1]} ({Doctors_DataBase[doc][0][0]})")
            elif choice == "B":
                break
            else:
                print("❌ Invalid choice.")

    else:
        print("❌ Please choose 1 or 2.")
