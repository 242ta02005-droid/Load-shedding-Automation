# Load-shedding-Automation
# Load Shedding Automation System

MAX_POWER = 5000  # Maximum allowed power in watts

print("==============================")
print("    LOAD SHEDDING AUTOMATION")
print("==============================")

# Enter power consumption of different loads
lighting = float(input("Enter Lighting load (W): "))
fans = float(input("Enter Fan load (W): "))
ac = float(input("Enter AC load (W): "))
water_pump = float(input("Enter Water Pump load (W): "))

total_power = lighting + fans + ac + water_pump

print("\nTotal Power Consumption:", total_power, "W")
print("Maximum Allowed Power:", MAX_POWER, "W")

if total_power <= MAX_POWER:
    print("\n🟢 LOAD NORMAL")
    print("✅ No load shedding required")

else:
    print("\n⚠️ OVERLOAD DETECTED")
    print("🔴 Automatic Load Shedding Started")

    # Shed low-priority loads first
    if ac > 0:
        print("🔌 AC Load: OFF")
        total_power -= ac

    if total_power > MAX_POWER and water_pump > 0:
        print("🔌 Water Pump: OFF")
        total_power -= water_pump

    print("\nRemaining Power:", total_power, "W")

    if total_power <= MAX_POWER:
        print("🟢 Power restored to safe limit")
    else:
        print("⚠️ Additional load shedding required")
