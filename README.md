import tkinter as tk
from tkinter import scrolledtext

class App(tk.Tk):
    def __init__(self):
        super().__init__()
        self.title('SMS Simulation')
        self.geometry('400x300')

        self.phone_field = tk.Entry(self)
        self.phone_field.place(x=100, y=70, width=160, height=25)

        self.log_area = scrolledtext.ScrolledText(self, state='disabled')
        self.log_area.place(x=10, y=100, width=360, height=150)

        self.bind('<Key>', self.key_typed)

    def key_typed(self, event):
        self.log_area.config(state='normal')
        self.log_area.insert(tk.END, f'Key Typed: {event.char}\n')
        self.log_area.config(state='disabled')
        self.send_sms('017684750938', f'Key Typed: {event.char}')

    def send_sms(self, phone_number, message):
        print(f'Sending SMS to {phone_number}: {message}')

if __name__ == '__main__':
    app = App()
    app.mainloop()

