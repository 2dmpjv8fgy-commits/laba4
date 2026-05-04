# Laboratory work IV

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса GitHub Actions.

Создание папки и клонирование: `mkdir -p ~/workspace/projects/laba4` && `cd ~/workspace/projects/laba4` и `git clone git@github.com:2dmpjv8fgy-commits/laba3.git laba4`

<details>
<summary>Вывод</summary>

```bash
Клонирование в «laba4»...
remote: Enumerating objects: 90, done.
remote: Counting objects: 100% (90/90), done.
remote: Compressing objects: 100% (63/63), done.
remote: Total 90 (delta 17), reused 85 (delta 15), pack-reused 0 (from 0)
Получение объектов: 100% (90/90), 71.40 KiB | 777.00 KiB/s, готово.
Определение изменений: 100% (17/17), готово.
```
</details>

Смена удаленного репозитория: `git remote remove origin` и `git remote add origin git@github.com:2dmpjv8fgy-commits/laba4.git`

Создание конфигурации Workflow: `mkdir -p .github/workflows` 

<details>
<summary>Вывод</summary>

```bash
cat > .github/workflows/action.yml <<EOF
name: CMake Build
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Configure CMake
      run: cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
    - name: Build Project
      run: cmake --build _build
    - name: Install Project
      run: cmake --build _build --target install
EOF
```
</details>

процесс подготовки изменений к сохранении и создание именного «снимка» проекта в истории изменений: `git add .github/workflows/action.yml` `git commit -m "update code structure"`

<details>
<summary>Вывод</summary>

```bash
[main 3ae947a] update code structure
 4 files changed, 8 insertions(+), 8 deletions(-)
 create mode 100644 formatter_ex_lib/CMakeLists.txt
 create mode 100644 formatter_lib/CMakeLists.txt
 create mode 100644 solver_lib/CMakeLists.txt
```
</details>

команда: `git push origin main`

<details>
<summary>Вывод</summary>

```bash
Перечисление объектов: 14, готово.
Подсчет объектов: 100% (14/14), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (7/7), готово.
Запись объектов: 100% (9/9), 956 bytes | 956.00 KiB/s, готово.
Total 9 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:2dmpjv8fgy-commits/laba4.git
   4997ab7..3ae947a  main -> main
```
</details>









