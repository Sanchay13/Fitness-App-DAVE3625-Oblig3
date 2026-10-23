# Fuel & Burn

Fuel & Burn is a simple fitness app that helps you keep track of your calories. You log the dishes you have eaten and the exercise you have done, and the app works out how many calories you have left for the day. Based on your body and your goal (lose, maintain or gain weight), it estimates how much you should eat per day and shows your progress over time.

## Features

- **Today:** Add dishes from a list of common meals, or type your own. Log exercise and the app calculates calories burned from the activity, duration and your weight. A ring shows how much of today's budget is left. You can step back to earlier days.
- **Goals:** Enter sex, age, height, weight, activity level and goal. The app shows the calculation step by step (BMR → maintenance → daily target) and estimates when you will reach your target weight.
- **Logging streak:** Counts how many days in a row you have logged at least one meal or workout. It shows on the Today tab and under Progress, together with your best streak ever, and celebrates milestones like 3, 7 and 14 days. If you haven't logged today yet, the streak stays alive until midnight.
- **Progress:** A chart of calories eaten and burned over the last 14 days, a weight curve with your target weight, and key numbers for the past week.

## How the app calculates

- Basal metabolic rate (BMR) with the Mifflin–St Jeor equation.
- Maintenance = BMR × everyday activity factor.
- 1 kg of body fat ≈ 7,700 kcal, so 0.5 kg per week means a deficit of about 550 kcal per day.
- Exercise: MET value × weight (kg) × hours. Calories burned in exercise are added on top of the daily target.
- The app never sets a target below 1,200 kcal (women) / 1,500 kcal (men) per day.

The numbers are estimates, not medical advice.

## Technology

A single HTML file with HTML, CSS and plain JavaScript. No server, login or external libraries. Data is stored only in your own browser (localStorage), so no personal data is sent anywhere. The first time you open the app it shows 14 days of sample data, which you can delete with "Start with an empty app".

## Running the app

Open `index.html` in a browser, or publish the repository with GitHub Pages.

## How AI was used

The app was built with vibe coding together with Claude (Anthropic). I described the idea in my own words and the AI wrote the code. The app was then tested automatically in a browser (at both desktop and phone size), and the tests found bugs that were fixed:

- The tabs did not hide each other when the file was opened outside Claude.
- The weight chart was cut off at the right edge on narrow screens.
- The "days on target" statistic was too strict and was changed to "days within budget".
- During my own testing, the "Add food" button did nothing. The cause was that the browser blocked form submission in the frame the app runs in. The buttons were rewritten to use click handlers, and the app now shows a clear message if a field is missing (for example calories for a dish that is not in the list). Typing part of a name, like "taco", now also finds the dish.

The calorie formula was also checked against a value calculated by hand. After my first round of feedback I also asked the AI to add a logging streak to motivate daily use. Afterwards the whole app was translated from Norwegian to English, renamed from "Formkurve" to "Fuel & Burn", and tested again.
