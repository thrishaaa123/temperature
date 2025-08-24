import tkinter as tk
from tkinter import messagebox

# Conversion functions
def celsius_to_fahrenheit(c):
    return (c * 9/5) + 32

def celsius_to_kelvin(c):
    return c + 273.15

def fahrenheit_to_celsius(f):
    return (f - 32) * 5/9

def fahrenheit_to_kelvin(f):
    return (f - 32) * 5/9 + 273.15

def kelvin_to_celsius(k):
    return k - 273.15

def kelvin_to_fahrenheit(k):
    return (k - 273.15) * 9/5 + 32

# Main conversion function
def convert():
    try:
        temp = float(entry.get())
        choice = option.get()

        if choice == "Celsius to Fahrenheit":
            result = f"{temp}°C = {celsius_to_fahrenheit(temp):.2f}°F"
        elif choice == "Celsius to Kelvin":
            result = f"{temp}°C = {celsius_to_kelvin(temp):.2f}K"
        elif choice == "Fahrenheit to Celsius":
            result = f"{temp}°F = {fahrenheit_to_celsius(temp):.2f}°C"
        elif choice == "Fahrenheit to Kelvin":
            result = f"{temp}°F = {fahrenheit_to_kelvin(temp):.2f}K"
        elif choice == "Kelvin to Celsius":
            result = f"{temp}K = {kelvin_to_celsius(temp):.2f}°C"
        elif choice == "Kelvin to Fahrenheit":
            result = f"{temp}K = {kelvin_to_fahrenheit(temp):.2f}°F"
        else:
            result = "Invalid choice"

        # Pop up result
        messagebox.showinfo("Conversion Result", result)

    except ValueError:
        messagebox.showerror("Error", "Please enter a valid number!")

# Tkinter GUI
root = tk.Tk()
root.title("🌡 Temperature Converter")
root.geometry("400x200")

tk.Label(root, text="Enter Temperature:", font=("Arial", 12)).pack(pady=5)
entry = tk.Entry(root, font=("Arial", 12))
entry.pack(pady=5)

tk.Label(root, text="Select Conversion:", font=("Arial", 12)).pack(pady=5)
options = ["Celsius to Fahrenheit", "Celsius to Kelvin",
           "Fahrenheit to Celsius", "Fahrenheit to Kelvin",
           "Kelvin to Celsius", "Kelvin to Fahrenheit"]
option = tk.StringVar(root)
option.set(options[0])
tk.OptionMenu(root, option, *options).pack(pady=5)

tk.Button(root, text="Convert", command=convert, bg="green", fg="white", font=("Arial", 12)).pack(pady=10)

root.mainloop()
