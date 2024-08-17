import tkinter as tk
from tkinter import ttk
from datetime import datetime, timedelta
import random

class DeathDatePrediction:
    def _init_(self, root):
        self.root = root
        self.root.title("Death Date Prediction")

        self.label_birthdate = tk.Label(root, text="Enter your birthdate (YYYY-MM-DD):")
        self.label_birthdate.pack(pady=10)

        self.entry_birthdate = tk.Entry(root)
        self.entry_birthdate.pack(pady=5)

        self.predict_button = tk.Button(root, text="Predict Death Date", command=self.predict_death_date)
        self.predict_button.pack(pady=10)

        self.result_label = tk.Label(root, text="")
        self.result_label.pack(pady=10)

    def predict_death_date(self):
        birthdate_str = self.entry_birthdate.get()
        try:
            birthdate = datetime.strptime(birthdate_str, "%Y-%m-%d")
            # Randomly add 60 to 90 years
            years_to_add = random.randint(60, 90)
            death_date = birthdate + timedelta(days=years_to_add * 365.25)
            self.result_label.config(text=f"Predicted Death Date: {death_date.strftime('%Y-%m-%d')}")
        except ValueError:
            self.result_label.config(text="Invalid date format. Please use YYYY-MM-DD.")

if _name_ == "_main_":
    root = tk.Tk()
    app = DeathDatePrediction(root)
    root = tk.Tk()
    app = DeathDatePrediction(root)
    root.mainloop()
