# Calories Python Calculator

##  Mifflin-St Jeor
*The Mifflin-St Jeor equation is a widely used tool to determine the resting metabolic rate [RMR], which is defined as the number of calories burned while the body is in complete rest.
RMR is also known as resting energy expenditure [REE]. The equation was developed by MD Mifflin and ST St Jeor and first introduced in a paper published in 1990.
There are several equations for measuring RMR, including the most popular Harris-Benedict equation which was developed in 1919 and revised for accuracy in 1984.
A comparative study of four predictive equations found that the Mifflin-St Jeor equation is more likely than the other equations to predict RMR to within 10% of that measured.
The Mifflin-St Jeor formula, the most reliable and accurate equation, according to the systematic review published by the Journal of the Academy of Nutrition and Dietetics in 2005, this equation depends on a group of elements, namely; `Age`, `height`, and `weight`, in addition to `gender`, the mathematical formulas used to calculate the basal metabolic rate (`BMR`) for males and females, as follows:*

## Equation

* **Females** =  $10 \times weight [kg] + 6.25 \times height [cm] - 5 \times age [years] - 161$
* **Males** = $10 \times weight [kg] + 6.25 \times height [cm] - 5 \times age [years] + 5$

*Multiply by scale factor for activity level:*
* Sedentary $\times 1.25$
* Light active $\times 1.375$
* Moderately active   $\times 1.55$
* Active $\times 1.725$


## References

* Mifflin MD, St Jeor ST, Hill LA, Scott BJ, Daugherty SA, Koh YO. A new predictive equation for resting energy expenditure in healthy individuals. Am J Clin Nutr. 1990;51(2):241-7. doi: 10. 093/ajcn/51.2.241.
Frankenfield D, Roth-Yousey L, Compher C.

* Comparison of predictive equations for resting metabolic rate in healthy nonobese and obese adults: a systematic review. J Am Diet Assoc. 2005;105(5):775-89. doi: 10.1016/j.jada.2005.02.005.
* The Mifflin-St Jeor Equation calculator is created by QxMD.


## Defining Main Function

```py
def main():
    welcome()
    gender = sex()
    weight = get_weight()
    height = get_height()
    age = get_age()
    rest_bmr = calculate_bmr(gender, weight, height, age) 
    total_calculation(rest_bmr)
```

## Little introduction

```py
def welcome():
    print("Welcome to your calories python calculator!\nFind out How many calories should you eat daily.\n")
```

## Ask for user gender

```py
def sex():
    sexes = ["male","female","M","F","f","m","Male","Female"]
    while True:
        sex = str(input("Do you identify as male or female? "))
        while sex not in sexes:
            sex = str(input("Please enter either 'male' or 'female' "))
        else:
            return sex
            break
```

## Get user weight in Kg

```py
def get_weight():
    weight_kg = float(input("Enter your weight in kilograms: "))
    while weight_kg <= 0:
        weight_kg = float(input("Invalid input. Please enter your weight in kilograms: "))
    else:
        return weight_kg
```

## Get user Height in Cm

```py
def get_height():
    height_cm = float(input("Enter your height in Centimeters: "))
    while height_cm <= 0:
        height_cm = float(input("Invalid input. Please enter your height in Centimeters: "))
    else:
        return height_cm
```

## Get user age in years

```py
def get_age():
    age_yrs = int(input("Enter your age in years: "))
    while age_yrs <= 0:
        age_yrs = int(input("Invalid Input. Please enter your age in years: "))
    else:
        return age_yrs
```

## BMR calculations for male or female

```py
def calculate_bmr(gender, weight, height, age):
    male = ["male", "M" , "m", "Male"]
    female = ["female", "F", "f", "Female"]
    if gender == female:
        women = (weight * 10) + (height * 6.25) - (age * 5) - 161
        return int(women)
    else:
        men = (weight * 10) + (height * 6.25) - (age * 5) + 5
        return int(men)
```

## calculate total daily calories based on bmr and and activity level

```py
def total_calculation(rest_bmr):
    user_activity_lvl = get_user_activity()    

    maintain = {
      "sedentary" : get_sedentary(rest_bmr), 
      "light" : get_light_activity(rest_bmr), 
      "moderate" : get_moderate_activity(rest_bmr), 
      "active" : get_very_active(rest_bmr)
      }

    if user_activity_lvl == "sedentary":
        print("You need to eat " + str(maintain["sedentary"]) + " calories a day to maintain your current weight")

    if user_activity_lvl == "light":
        print("You need to eat " + str(maintain["light"]) + " calories a day to maintain your current weight")

    if user_activity_lvl == "moderate":
        print("You need to eat " + str(maintain["moderate"]) + " calories a day to maintain your current weight")

    if user_activity_lvl == "active":
        print("You need to eat " + str(maintain["active"]) + " calories a day to maintain your current weight")
```


## Get user weekly activity levels

```py
def get_user_activity():
    activity_lvl = ["sedentary", "light", "moderate", "active"]
    while True:
        user_lvl = str(input("\nWhat is your activity level?\n\nSedentary is little to no exercise.\nLightly active is light exercise/sports 1 - 3 days/week.\nModerately active is moderate exercise/sports 3 - 5 days/week.\nVery active is hard exercise every day, or 2 xs/day 6 - 7 days/week.\n\nPlease enter: 'sedentary', 'light', 'moderate',  or 'active' "))
        
        while user_lvl not in activity_lvl:
            user_lvl = str(input( "Invalid input. Please enter: 'sedentary', 'light', 'moderate',  or 'active' "))
        else:
            return user_lvl
            break
```

## Multiply resting BMR by Activity levels

```py
def get_sedentary(rest_bmr):
    sedentary = rest_bmr * 1.25
    return sedentary

def get_light_activity(rest_bmr):
    light = rest_bmr * 1.375
    return light

def get_moderate_activity(rest_bmr):
    moderate = rest_bmr * 1.550
    return moderate

def get_very_active(rest_bmr):
    active = rest_bmr * 1.725
    return active
```

## In Python `“if__name__== “__main__” `allows you to run the Python files either as reusable modules or standalone programs.

```py
if __name__ == '__main__':
    main()
```
