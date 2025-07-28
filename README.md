def celsius_to_fahrenheit(celsius):
    return celsius * 9/5 + 32

def celsius_to_kelvin(celsius):
    return celsius + 273.15

def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

def fahrenheit_to_kelvin(fahrenheit):
    return (fahrenheit - 32) * 5/9 + 273.15

def kelvin_to_celsius(kelvin):
    return kelvin - 273.15

def kelvin_to_fahrenheit(kelvin):
    return (kelvin - 273.15) * 9/5 + 32

def convert_temperature(value, from_scale, to_scale):
    from_scale = from_scale.lower()
    to_scale = to_scale.lower()
    if from_scale == to_scale:
        return value
    if from_scale == 'celsius':
        temp_c = value
    elif from_scale == 'fahrenheit':
        temp_c = fahrenheit_to_celsius(value)
    elif from_scale == 'kelvin':
        temp_c = kelvin_to_celsius(value)
    else:
        raise ValueError(f"Unknown temperature scale: {from_scale}")

    if to_scale == 'celsius':
        return temp_c
    elif to_scale == 'fahrenheit':
        return celsius_to_fahrenheit(temp_c)
    elif to_scale == 'kelvin':
        return celsius_to_kelvin(temp_c)
    else:
        raise ValueError(f"Unknown temperature scale: {to_scale}")

if __name__ == '__main__':
    print("Temperature Converter")
    print("Valid scales: Celsius, Fahrenheit, Kelvin")
    value = float(input("Enter the temperature value: "))
    from_scale = input("Convert from (Celsius/Fahrenheit/Kelvin): ").strip()
    to_scale = input("Convert to (Celsius/Fahrenheit/Kelvin): ").strip()
    try:
        result = convert_temperature(value, from_scale, to_scale)
        print(f"{value} {from_scale.capitalize()} = {result:.2f} {to_scale.capitalize()}")
    except ValueError as e:
        print(e)
