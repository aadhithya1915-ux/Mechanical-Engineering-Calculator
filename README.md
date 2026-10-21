import math

def force():
    mass = float(input("Enter mass (kg): "))
    acceleration = float(input("Enter acceleration (m/s^2): "))
    print(f"Force = {mass * acceleration:.2f} N")

def stress():
    force_value = float(input("Enter force (N): "))
    area = float(input("Enter cross-sectional area (mm^2): "))
    if area <= 0:
        print("Area must be positive.")
        return
    stress_mpa = force_value / area
    print(f"Normal stress = {stress_mpa:.2f} MPa")

def pressure():
    force_value = float(input("Enter force (N): "))
    area = float(input("Enter area (m^2): "))
    if area <= 0:
        print("Area must be positive.")
        return
    print(f"Pressure = {force_value / area:.2f} Pa")

def torque():
    force_value = float(input("Enter force (N): "))
    radius = float(input("Enter perpendicular distance (m): "))
    print(f"Torque = {force_value * radius:.2f} N.m")

def power():
    torque_value = float(input("Enter torque (N.m): "))
    rpm = float(input("Enter rotational speed (RPM): "))
    angular_velocity = 2 * math.pi * rpm / 60
    print(f"Power = {torque_value * angular_velocity:.2f} W")

def density():
    mass = float(input("Enter mass (kg): "))
    volume = float(input("Enter volume (m^3): "))
    if volume <= 0:
        print("Volume must be positive.")
        return
    print(f"Density = {mass / volume:.2f} kg/m^3")

def kinetic_energy():
    mass = float(input("Enter mass (kg): "))
    velocity = float(input("Enter velocity (m/s): "))
    print(f"Kinetic energy = {0.5 * mass * velocity**2:.2f} J")

def gear_ratio():
    driver = int(input("Enter driving gear teeth: "))
    driven = int(input("Enter driven gear teeth: "))
    if driver <= 0 or driven <= 0:
        print("Tooth counts must be positive.")
        return
    print(f"Gear ratio = {driven / driver:.2f}:1")

calculators = {
    "1": ("Force", force),
    "2": ("Stress", stress),
    "3": ("Pressure", pressure),
    "4": ("Torque", torque),
    "5": ("Power", power),
    "6": ("Density", density),
    "7": ("Kinetic Energy", kinetic_energy),
    "8": ("Gear Ratio", gear_ratio),
}

def main():
    while True:
        print("\n=== MECHANICAL ENGINEERING CALCULATOR ===")
        for number, (name, _) in calculators.items():
            print(f"{number}. {name}")
        print("0. Exit")

        choice = input("Choose a calculator: ").strip()

        if choice == "0":
            print("Thank you for using the calculator!")
            break

        if choice not in calculators:
            print("Invalid choice. Please try again.")
            continue

        try:
            calculators[choice][1]()
        except ValueError:
            print("Invalid input. Please enter numeric values.")

if __name__ == "__main__":
    main()
