# Создание модуля на Python

Лучше сначала прочитать туториал по созданию модуля на C++, ибо идейно они не отличаются. 

Чтобы добавить модуль в систему робота, добавьте в файл `/home/nao/naoqi/preferences/autoload.ini` на роботе строчки:

        -> [user]
    
        -> /path/to/python_module.py

Кратно пробежимся по содержимому файла. 

- Класс HumanGreeter, наследованный от ALModule - реализует всю идею модуля. 
- функция main() привязывает модуль к брокеру.

В классе HumanGreeter присутствует метод onFaceDetected(). Это обработчик события, который срабатывает в случае, когда перед роботом появляется человек. 

Чтобы не принимать, а наоброт генерировать исключения нужны следующие строчки:

```
from naoqi import ALProxy

# create proxy on ALMemory
memProxy = ALProxy("ALMemory","localhost",9559)

#raise event. Data can be int, float, list, string
memProxy.raiseEvent("My event", "data")
```
P.S. В оригинальной документации написано следующее: "Обязательно пишите документирующие комментарии к методам класса. Иначе bind-метод не создастся и невозможно будет использовать его извне". Правдивость заявления на практике не подтвердилась. Но все же давайте их писать, ведь с ними проще и понятнее.

P.P.S. Под документирующими комментариями имеется в виду следующее:

```
def SomeMethod(args):
        '''Этот метод делает то самое'''
        some code 
        return result

```