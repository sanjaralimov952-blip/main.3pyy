# main.3pyy
import flet as ft
from datetime import datetime


def main(page: ft.Page):
    page.title = "Приветствие с временем"
    page.theme_mode = ft.ThemeMode.DARK

    greeting_text = ft.Text("Введите имя и нажмите кнопку")
    name_input = ft.TextField(label="Введите имя", width=300)

    def say_hello(e):
        if name_input.value:
            now = datetime.now()
            time_str = now.strftime("%Y:%m:%d - %H:%M:%S")
            greeting_text.value = f"{time_str} - Привет, {name_input.value}!"
            name_input.value = ""
            page.update()

    send_button = ft.ElevatedButton("Отправить", on_click=say_hello)
    name_input.on_submit = say_hello

    page.add(
        greeting_text,
        name_input,
        send_button
    )


ft.app(target=main)
