# Портфолио

## Карпенко Андрей Владимирович


## Образование

- Среднее общее
- Высшее образование
    - Сибирский Государственный Университет Телекоммуникаций и Информатики (СибГУТИ), на данный момент 2 курс


## Навыки в области программирования

- Python
    - Pygame
    - vk_api (бот ВК)
    - telebot (бот Телеграм)
    - pyautogui (автоматизация действий)
    - moderngl (написание шейдеров)
- C/C++
    - OpenGL
- R
    - Shiny (написание онлайн приложения для обработки данных)

## Выполненные проекты

### Bin_to_header

- Сохранение двоичного файла в массиве файла с указанным типом и расширением ".h"
- Полученный файл можно связать с main для последующего использования (например хранение зависимостей)

<img src = "example bin2header.png">




### Python shaders

Используются простые функции

```python
import moderngl_window as mglw
import time
class App(mglw.WindowConfig):
    window_size = 1600, 900
    resource_dir = 'programs'
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.quad = mglw.geometry.quad_fs()
        self.program = self.load_program(vertex_shader='vertex.glsl', fragment_shader='fragment.glsl')
        # uniforms
        self.program['u_resolution'] = self.window_size
        self.kpx = 0.0
        self.kpy = 0.0
        self.con = 0
        self.start_up = 0
        self.lim = 3
        self.dupy = 0.001
    def render(self, time, frame_time):
        self.ctx.clear()
        if(self.con == 1):
            self.UP_space()
        self.program['k_pl1'] = (self.kpx,self.kpy)
        self.quad.render(self.program)
    def mouse_position_event(self, x, y, dx, dy):
        self.program['u_mouse'] = (x, y)
    def key_event(self, key, action, modifiers):
        keys = self.wnd.keys
        if key == keys.D:
            self.kpx += 0.05
        if key == keys.A:
            self.kpx -= 0.05
        if key == keys.SPACE:
            self.start_up = time.time()
            self.con = 1
    def UP_space(self):
        if( self.con == 1 and self.lim > time.time()-self.start_up):
            self.kpy += self.dupy
            if(self.lim/2 > time.time()-self.start_up):
                self.dupy = -0.001
        else:
            self.con = 0
if __name__ == '__main__':
    mglw.run_window_config(App)

```
<img src = "example 3d.png">



### Журнал оценок

Онлайн приложение для редактирования, сохранения, отображение статистики загруженного файла

<a href="https://waffles.shinyapps.io/app074/">Ссылка на приложение</a>

<img src = "example r_shiny.png">








