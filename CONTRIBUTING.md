# f250_tracker.py

# --- CONSTANTS (You can adjust these) ---
# Average F-250 Curb Weight (varies by model/options)
F250_CURB_WEIGHT_LBS = 7000 
# Suggested maintenance cost per kilometer for wear and tear fund
MAINTENANCE_RATE_PER_KM = 0.15 
# Base price for taxi/hauling fare
FARE_BASE_PRICE = 5.00
# Price per kilometer for taxi/hauling fare
FARE_RATE_PER_KM = 1.50

# ----------------------------------------------------
# --- FUNCTION 1: Fuel & Mileage Calculations ---
# ----------------------------------------------------
def fuel_and_mileage_calc():
    """Calculates L/100km and cost per kilometer."""
    print("\n--- Fuel & Mileage Calculator ---")
    
    try:
        # Get user input
        distance_km = float(input("Enter distance traveled (km): "))
        fuel_consumed_liters = float(input("Enter fuel consumed (Liters): "))
        fuel_price_per_liter = float(input("Enter fuel price per liter: "))
        
        # Calculate L/100km
        liters_per_100km = (fuel_consumed_liters / distance_km) * 100
        
        # Calculate Total Cost and Cost per km
        total_fuel_cost = fuel_consumed_liters * fuel_price_per_liter
        cost_per_km = total_fuel_cost / distance_km
        
        print("\n*** Results ***")
        print(f"Fuel Consumption: {liters_per_100km:.2f} L/100km")
        print(f"Total Fuel Cost: ${total_fuel_cost:.2f}")
        print(f"Cost per Kilometer: ${cost_per_km:.3f}")
        
    except ValueError:
        print("Error: Please enter valid numbers for all inputs.")

# ----------------------------------------------------
# --- FUNCTION 2: Wear & Tear Fund Calculation ---
# ----------------------------------------------------
def wear_and_tear_calc():
    """Calculates suggested funds to set aside for maintenance."""
    print("\n--- Wear & Tear Fund Calculator ---")
    
    try:
        distance_km = float(input("Enter distance driven (km) since last maintenance check: "))
        
        # Calculate suggested fund amount
        fund_amount = distance_km * MAINTENANCE_RATE_PER_KM
        
        print("\n*** Results ***")
        print(f"Suggested Maintenance Rate: ${MAINTENANCE_RATE_PER_KM:.2f} per km")
        print(f"Based on {distance_km:.0f} km, set aside: ${fund_amount:.2f}")
        
    except ValueError:
        print("Error: Please enter a valid number for distance.")

# ----------------------------------------------------
# --- FUNCTION 3: Weight and Distribution Calculations ---
# ----------------------------------------------------
def weight_calc():
    """Calculates total combined weight and estimates tongue/hitch weight."""
    print("\n--- Weight & Distribution Calculator (LBS) ---")
    
    try:
        # Get user input
        trailer_weight_lbs = float(input("Enter total trailer/cargo weight (lbs): "))
        
        # 1. Total Combined Weight
        total_combined_weight = F250_CURB_WEIGHT_LBS + trailer_weight_lbs
        
        # 2. Estimated Tongue/Hitch Weight
        # Standard range for tongue weight is 10% to 15% of total trailer weight.
        # We'll calculate both to show the safe range.
        tongue_min_lbs = trailer_weight_lbs * 0.10
        tongue_max_lbs = trailer_weight_lbs * 0.15
        
        print("\n*** Results (LBS) ***")
        print(f"F-250 Curb Weight (Assumed): {F250_CURB_WEIGHT_LBS:.0f} lbs")
        print(f"Trailer/Cargo Weight: {trailer_weight_lbs:.0f} lbs")
        print(f"Total Combined Weight (Approx.): {total_combined_weight:.0f} lbs")
        print("\n--- Weight Distribution Guide ---")
        print(f"Required Tongue Weight Range (10-15%): {tongue_min_lbs:.0f} lbs to {tongue_max_lbs:.0f} lbs")
        print("Note: Ensure your hitch rating can handle this tongue weight.")
        
    except ValueError:
        print("Error: Please enter a valid number for trailer weight.")

# ----------------------------------------------------
# --- FUNCTION 4: Hauling/Taxi Fares Calculation ---
# ----------------------------------------------------
def fare_calc():
    """Calculates an estimated fare based on distance."""
    print("\n--- Hauling/Taxi Fare Calculator ---")
    
    try:
        distance_km = float(input("Enter trip distance (km): "))
        
        # Calculate total fare
        total_fare = FARE_BASE_PRICE + (distance_km * FARE_RATE_PER_KM)
        
        print("\n*** Results ***")
        print(f"Base Fare Price: ${FARE_BASE_PRICE:.2f}")
        print(f"Rate Per Kilometer: ${FARE_RATE_PER_KM:.2f}")
        print(f"Total Estimated Fare for {distance_km:.1f} km: ${total_fare:.2f}")
        
    except ValueError:
        print("Error: Please enter a valid number for distance.")


# ----------------------------------------------------
# --- MAIN APPLICATION LOOP (Menu) ---
# ----------------------------------------------------
def main_menu():
    """Displays the main menu and handles user selection."""
    while True:
        print("\n===================================")
        print("      F250 UTILITY TRACKER")
        print("===================================")
        print("1. Fuel & Mileage Calculator (L/100km)")
        print("2. Wear & Tear Fund Calculator")
        print("3. Weight & Distribution Calculator (LBS)")
        print("4. Hauling/Taxi Fare Calculator")
        print("5. Exit")
        
        choice = input("Enter your choice (1-5): ")
        
        if choice == '1':
            fuel_and_mileage_calc()
        elif choice == '2':
            wear_and_tear_calc()
        elif choice == '3':
            weight_calc()
        elif choice == '4':
            fare_calc()
        elif choice == '5':
            print("Exiting F250 Utility Tracker. Happy hauling!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")

# Start the application
if __name__ == "__main__":
    main_menu()
# Contributing

BeeWare <3's contributions!

Please be aware that BeeWare operates under a [Code of
Conduct](https://beeware.org/community/behavior/code-of-conduct/).

If you'd like to contribute to Briefcase development, our [contribution
guide](https://briefcase.readthedocs.io/en/latest/how-to/contribute/index.html) details how
to set up a development environment, and other requirements we have as part of our
contribution process.
