# 🔧 ***builder***

## 🛠️ Инструменты для генерации библиотеки

### 📋 Порядок действий (работать в папке `builder` при активированном `venv`):

1. **Для запуска MakeFile командой make из VSCode нужно установить через PowerShell или cmd:**

    - winget install GnuWin32.Make.

2. **Создание зависимостей для работы сборки библиотеки:**

    ```bash
        pip install -r requirements_builder.txt  
    ```

3. **Создание зависимостей Pipfile и Pipfile.lock для библиотеки (в случае отсутствия или создания новых зависимостей):**

    ```bash
        pipenv install requirements.txt  
    ```

4. **В папке проекта pachca_code_gen_team2 в файле .env указать:**
    - PACKAGE_VERSION=<Версия пакета>
    - TWINE_USERNAME=<Имя пользвателя сервиса TestPyPI>
    - TWINE_API_TOKEN=<Токен пользвателя сервиса TestPyPI>

5. **Запуск создания и загрузки библиотеки на сервис TestPyPI при помощи команды:**

    ```bash
        make upload
    ```
6. **Установка библиотеки с сериса TestPyPI:**

    ```bash
        pip install --no-cache-dir -i https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple/ PachcaAPI==0.1.1
    ```

7. **Запуск генератора и тестов:**

    - run_generate_and_test     - запуск генератора и тестов
    - run_generator             - запуск генератора
    - run_test                  - запуск тестов

## 📂 Структура генератора

_src/builder/_

#### 📜 requirements_builder.txt
- файл со списком пакетов или библиотек, необходимых для работы упаковщика библиотеки.

#### 📜 requirements.txt
- файл со списком пакетов или библиотек, необходимых для работы над библиотек.

#### 📄 Pipfile
- файл, используемый виртуальной средой Pipenv для управления зависимостями библиотек.

#### 🔒 Pipfile.lock
- файл в формате JSON хранит контрольные суммы пакетов, которые устанавливаются в проект, что даёт гарантию, что развёрнутые на разных машинах окружения будут идентичны друг другу. 

#### 🛠️ Makefile 
- файл с инструкциями для утилиты make, которая нужна для автоматической сборки проекта.

#### 📦 setup.py
- файл с описанием, каким именно образом будет упакован код для медотов генерации

#### 🔗 MANIFEST.in
- файл с указанием, какие файлы следует включить в сборку пакета
