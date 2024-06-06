1-Defining the class or method for calculating the survival duration

To encapsulate the logic for calculating the survival duration in a more structured and reusable way, we can define a class called SurvivalDurationCalculator. This class will contain methods to set the age, select the desired time units, perform the calculations, and display the results.

Here is how you can define the class:

SurvivalDurationCalculator Class
class SurvivalDurationCalculator:
    # Constants for time unit conversions
    MONTHS_IN_YEAR = 12
    WEEKS_IN_YEAR = 52.1429  # Average weeks in a year
    DAYS_IN_YEAR = 365.25  # Average including leap years
    HOURS_IN_DAY = 24
    MINUTES_IN_HOUR = 60
    SECONDS_IN_MINUTE = 60

    def __init__(self, age_years):
        """
        Initializes the calculator with the given age in years.
        :param age_years: Age in years (can be a float to handle fractions)
        """
        self.age_years = age_years
        self.durations = {}

    def calculate_durations(self, units):
        """
        Calculate the duration in different time units.
        :param units: List of units to calculate (e.g., ['years', 'months', 'days'])
        """
        self.durations = {}

        # Calculate duration in each unit
        if 'years' in units:
            self.durations['years'] = self.age_years
        if 'months' in units:
            self.durations['months'] = self.age_years * self.MONTHS_IN_YEAR
        if 'weeks' in units:
            self.durations['weeks'] = self.age_years * self.WEEKS_IN_YEAR
        if 'days' in units:
            self.durations['days'] = self.age_years * self.DAYS_IN_YEAR
        if 'hours' in units:
            self.durations['hours'] = self.age_years * self.DAYS_IN_YEAR * self.HOURS_IN_DAY
        if 'minutes' in units:
            self.durations['minutes'] = self.age_years * self.DAYS_IN_YEAR * self.HOURS_IN_DAY * self.MINUTES_IN_HOUR
        if 'seconds' in units:
            self.durations['seconds'] = self.age_years * self.DAYS_IN_YEAR * self.HOURS_IN_DAY * self.MINUTES_IN_HOUR * self.SECONDS_IN_MINUTE

    def get_durations(self):
        """
        Get the calculated durations.
        :return: Dictionary of calculated durations in selected units
        """
        return self.durations

    def display_durations(self):
        """
        Display the calculated durations in a readable format.
        """
        print("\nThe duration lived is:")
        for unit, value in self.durations.items():
            print(f"{value:,.2f} {unit}")


# Example usage:
def main():
    print("Survival Duration Calculator")
    age_years = float(input("Enter age in years: "))

    print("Select the units for the duration (comma-separated list):")
    print("Options: years, months, weeks, days, hours, minutes, seconds")
    units_input = input("Units: ").lower()
    units = [unit.strip() for unit in units_input.split(',')]

    # Initialize calculator with age
    calculator = SurvivalDurationCalculator(age_years)
    # Calculate durations in selected units
    calculator.calculate_durations(units)
    # Display the results
    calculator.display_durations()

if __name__ == "__main__":
    main()
Explanation of the Class and Methods
Class Constants:

MONTHS_IN_YEAR, WEEKS_IN_YEAR, DAYS_IN_YEAR, HOURS_IN_DAY, MINUTES_IN_HOUR, and SECONDS_IN_MINUTE are class-level constants that define conversion rates.
__init__ Method:

Initializes the calculator with an age_years parameter, which is the person's age in years.
calculate_durations Method:

Takes a list of time units and calculates the duration lived in each unit. It stores the results in a dictionary self.durations.
get_durations Method:

Returns the dictionary of calculated durations.
display_durations Method:

Prints the calculated durations in a user-friendly format.
Usage Example
In the main function:

The user is prompted to enter their age and the desired time units.
An instance of SurvivalDurationCalculator is created with the given age.
The calculate_durations method calculates the durations in the specified units.
The display_durations method prints the results.
This structure allows for easy extension and modification of the code, and the class can be reused in different contexts, such as in a graphical user interface (GUI) or a web application.

2-Defining the logic for calculating the duration in 6 units 

To define the logic for calculating the duration in six specific units—years, months, weeks, days, hours, and seconds—we need to ensure our class handles these conversions accurately. Below is the refined Python class SurvivalDurationCalculator that calculates the duration a person has lived in the specified six units.

SurvivalDurationCalculator Class

class SurvivalDurationCalculator:
    # Constants for time unit conversions
    MONTHS_IN_YEAR = 12
    WEEKS_IN_YEAR = 52.1429  # Average weeks in a year (365.25 days / 7)
    DAYS_IN_YEAR = 365.25  # Average including leap years
    HOURS_IN_DAY = 24
    MINUTES_IN_HOUR = 60
    SECONDS_IN_MINUTE = 60

    def __init__(self, age_years):
        """
        Initializes the calculator with the given age in years.
        :param age_years: Age in years (can be a float to handle fractions)
        """
        self.age_years = age_years
        self.durations = {}

    def calculate_durations(self):
        """
        Calculate the duration in the specified six time units.
        """
        # Calculate duration in each unit
        self.durations['years'] = self.age_years
        self.durations['months'] = self.age_years * self.MONTHS_IN_YEAR
        self.durations['weeks'] = self.age_years * self.WEEKS_IN_YEAR
        self.durations['days'] = self.age_years * self.DAYS_IN_YEAR
        self.durations['hours'] = self.age_years * self.DAYS_IN_YEAR * self.HOURS_IN_DAY
        self.durations['seconds'] = (self.age_years * self.DAYS_IN_YEAR *
                                     self.HOURS_IN_DAY * self.MINUTES_IN_HOUR *
                                     self.SECONDS_IN_MINUTE)

    def get_durations(self):
        """
        Get the calculated durations.
        :return: Dictionary of calculated durations in selected units
        """
        return self.durations

    def display_durations(self):
        """
        Display the calculated durations in a readable format.
        """
        print("\nThe duration lived is:")
        for unit, value in self.durations.items():
            print(f"{value:,.2f} {unit}")


# Example usage:
def main():
    print("Survival Duration Calculator")
    age_years = float(input("Enter age in years: "))

    # Initialize calculator with age
    calculator = SurvivalDurationCalculator(age_years)
    # Calculate durations in specified units
    calculator.calculate_durations()
    # Display the results
    calculator.display_durations()

if __name__ == "__main__":
    main()
Explanation of the Class and Methods
Class Constants:

MONTHS_IN_YEAR, WEEKS_IN_YEAR, DAYS_IN_YEAR, HOURS_IN_DAY, MINUTES_IN_HOUR, and SECONDS_IN_MINUTE are constants that define conversion rates for the calculations.
__init__ Method:

Initializes the SurvivalDurationCalculator with the age in years. The age_years parameter can be a float to accommodate fractional years.
calculate_durations Method:

Calculates the duration a person has lived in six specific time units: years, months, weeks, days, hours, and seconds.
The method populates the self.durations dictionary with the calculated values for each unit.
get_durations Method:

Returns the dictionary of calculated durations. This method can be useful for retrieving the values programmatically.
display_durations Method:

Prints the calculated durations in a user-friendly format. Each duration is displayed with commas for thousands and two decimal places for better readability.
Example Usage
In the main function:

The user is prompted to enter their age in years.
An instance of SurvivalDurationCalculator is created using the input age.
The calculate_durations method is called to compute the durations in the six units.
The display_durations method prints the results.
Conversion Logic
Here’s a detailed breakdown of the conversion logic used in the calculate_durations method:

Years to Months: Multiply by 12.
Years to Weeks: Multiply by 52.1429 (average weeks in a year).
Years to Days: Multiply by 365.25 (average days in a year including leap years).
Years to Hours: Multiply by days per year (365.25) and hours per day (24).
Years to Seconds: Multiply by days per year, hours per day, minutes per hour, and seconds per minute.
This structure ensures the calculations are accurate and the code is easy to understand and maintain.














