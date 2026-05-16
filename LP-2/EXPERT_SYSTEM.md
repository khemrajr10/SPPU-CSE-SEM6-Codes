
Practical6_expertSystem

 Implement any one of the following Expert System:
 Hospitals and medical facilities 

Code:

# ---------------------------------------------------
# Expert System for Hospitals and Medical Facilities
# ---------------------------------------------------

print("======================================")
print("  Medical Expert System")
print("======================================")

# Take symptoms from user
fever = input("Do you have fever? (yes/no): ").lower()

cough = input("Do you have cough? (yes/no): ").lower()

headache = input("Do you have headache? (yes/no): ").lower()

stomach_pain = input("Do you have stomach pain? (yes/no): ").lower()

# Rule-Based Decision Making

# Condition for Flu
if fever == "yes" and cough == "yes":

    print("\nExpert System Result:")
    print("You may have Flu.")
    print("Suggested Medicine: Paracetamol")
    print("Advice: Drink plenty of water and take rest.")

# Condition for Migraine
elif headache == "yes" and fever == "no":

    print("\nExpert System Result:")
    print("You may have Migraine.")
    print("Suggested Medicine: Pain Reliever")
    print("Advice: Avoid stress and take proper sleep.")

# Condition for Food Poisoning
elif stomach_pain == "yes" and fever == "yes":

    print("\nExpert System Result:")
    print("You may have Food Poisoning.")
    print("Advice: Consult doctor immediately.")

# No matching disease
else:

    print("\nExpert System Result:")
    print("Symptoms not clearly identified.")
    print("Please consult a doctor.")
