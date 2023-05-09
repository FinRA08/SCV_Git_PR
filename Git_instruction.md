![Logo](unnamed.jpg)
# Работа с Git и GitHub

## 1. Проверка наличия установленного Git

В терминале выапполнить команду `git --version`. Если Git установлен, появится сообщение с информацией о версии программы, иныче будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git с сайта https://git-scm.com/downloads.
Устанавливаем с настройками по умолчанию.

## 3. Настройка Git

При первом использовании Git необходимо представится. Для этого нужно выполнить в терминале две команды:
```C#
git config --global user.name «Ваше имя английскими буквами»
git config --global user.email ваша почта@example.com
```

## 4. Создание репозитория в Git

Чтобы начать слежение за существующим проектом, перейдите в папку этого проекта и введите команду:
```C#
git init
```
В результате в существующей папке появится еще одна папка с именем `.git` и всеми 
нужными вам файлами репозитория — это будет основа вашего Git-репозитория.

## 5. Проверка состояния файлов - git status

Основным инструментом определения состояния файлов является команда 
`git status`. Данная команда позволяет определить отслеживаются ли изменения в файле, а так также изменения с первыичным документом, которые в последующем можно записать.

## 6. Слежение за новым файлом

Чтобы начать слежение за новым файлом, воспользуйтесь командой `git add` с указанием наименования фала (полное название писать не обязательно, при вводе  первых букв необходимо нажать `Tab`, для автоматического заполнения). Команда git
add работает с маршрутом доступа к файлу или к папке; если указан путь к папке, 
команда рекурсивно добавляет все находящиеся в ней файлы. 

## 7. Фиксация изменений

После того как область индексирования настроена нужным вам образом, можно 
зафиксировать внесенные туда изменения. 
```
!!!Важно, что все, оставленное неиндесированным, в том числе любые созданные или измененные файлы, для которых 
после редактирования не была выполнена команда git add, в текущию фиксацию не 
войдет. Все эти файлы останутся на вашем диске как измененные
```
Для проведения фиксации измениня данных, необходимо выпонить команду `git commit`. В целях маркирования изменений необходимо при фиксации, оставлять коментарий в качестве метки произведенных изменений, делается это с помощью добавления к команде `git commit` следующего: ` -m "Коментарий"`
```
Можно так же провести индексирование и фиксацию изменений с помощью одной команды git commit -a -m "Коментарий"
```

## 8. Просмотр истории версий

После сохранения нескольких версий файлов или клонирования уже имеющего 
содержимое репозитория, можно изучить, что было сделано ранее. Базовым и самым мощным инструментом в данном случае является 
команда `git log`.
По умолчанию при отсутствии параметров команда git log выводит в обратном 
хронологическом порядке список сохраненных в данный репозиторий версий.

У команды `git log` существует великое множество параметров, позволяющих 
вывести именно ту информацию, которая требуется. Рассмотрим несколько 
самых популярных.

Одним из самых полезных является параметр -p, показывающий разницу, внесеную каждым коммитом. А дополнительный параметр -2 ограничивает выводимый 
результат последними двумя записями.

Для получения краткой 
статистики по каждой версии применяется параметр `--stat`.

Еще одним крайне полезным параметром является `--pretty`. Он меняет формат 
вывода информации. Есть несколько предустановленных вариантов. Параметр 
`oneline` выводит каждый коммит в одну строку, что весьма удобно при просмотре 
большого числа коммитов. 
Пример команды -  `git log --pretty=oneline`.

## 9.Переход от одного коммита к другому

Переход на существующую ветку реализует команда `git checkout` с указаним хэш кода коммита (Узнать хэш код коммита, можно запросив сведения о изменениях через команду `git log`, для запуска команды достаточно первых четырех значений хэш кода).
Для возврата к последней версии файла, можно использовать команды `git checkout master` или `git switch`.

## 10. Сравнение между текущим файлом и закоммиченным фалом.

Для того что бы увидеть разницу между текущим файлом и закоммиченным файлом
используется команда `git diff`. При вызове указанной команды можно просмотреть внесенные изменения в файл, после последнего коммита, для понимания того какая работа была проделана, после последнего коммита.  

## 11.Игнорирование файлов
Для того, чтобы исключить из отслеживания, в репозитории определенные файлы или папки необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответсвующие таким файлам или папкам.

## 12. Создание веток в Git
По умолчанию имя основной ветки в Git - `master`.
Создать ветку можно командой:
```
git branch <имя новой ветки>

или

git checkout -b "имя новой ветки"

с помощью последней команды Вы сразу перейдете на новую ветку
```
Список веток в репозитории можно посмотреть с помощью команды `git branch`. Текущая ветка будет отмечена звездочкой **\*master**
Для переключения между ветками используется команда:
```
git checkout <имя ветки>
```
Важно!!!
```
Важно понимать, что переход на другую ветку сопровождается сменой файлов в рабочей 
папке. При возвращении в более старую ветку содержимое рабочей папки приобретет 
тот вид, который оно имело перед последним коммитом в этой ветке. Если система Git не 
сможет вернуть файлы в это состояние, она просто не даст вам выполнить переключение.
```

## 13. Слияние веток
Для слияния веток достаточно перейти в ветку, с которой будет осуществляться слияние, и воспользоваться командой `git merge <название ветки>`.

При выполнении указанной команды в текущую ветку будет добавлено содиржимое ветки указанной при вводе команды `git merge`.
```
Важно перед слиянием убедится что Вы находитесь в нелбходимой для слияния ветки.
```

## 14. Разрешение конфликтов

Процесс слияния далеко не всегда проходит гладко. Если в двух ветках, которые вы собираетесь слить, вы внесли разные изменения в один и тот же файл, Git не сможет просто взять и объединить их Git сообщит о конфликте и предложит выбрать, какие же изменения записать. Все, что относится к области конфликта слияния, помечено как неслитое `unmerged`. Система Git добавляет к проблемным файлам стандартные метки, позволяющие открывать эти файлы вручную и разрешать конфликты.
Версия с указателем текущей ветки (так как именно в нее вы перешли перед выполнением команды merge) располагается в верхней части блока (то есть выше набора символов =======), а версия из ветки из которой идет слияние показана в нижней части. Для разрешения конфликта Вам необходимо выбрать один из вариантов:
* 1. Оставить вариент данныйх из ветки в которую идет слияние;
* 2. Заменить данные в текущей ветки, данными из ветки слияния;
* 3. Сохранить данные из обоих веток (При этом данные из ветки в которую проходит слияние будут размещены в верхней части, а данные из ветки слияния будут размещены под данными текущей ветки);
* 4. Отменить слияние.

Если вы довольны полученным результатом и удостоверились в том, что все ранее конфликтовавшие файлы проиндексированы, остается завершить слияние командой `git commit`.

## 15. Удаление веток
Для удаления не используемых ветое используется команда `git
branch -d <Название ветки>`. Где параметр `d` сокращение от deleted (с англ. удалить).

В случае если ветка не слита, то команда `git
branch -d` не будет выполнена и git уведомит Вас о том, что данная ветка не слита. Для принудительного удалениея не слитой ветки используется аналогичная команда, только в место прописной `-d` указывается заглавная `-D`. В связи с чем, во избежание потери данных, рекомендуется всегда использовать `-d`.

## 16. Работа с удаленными репозиториями

Для работы с удаленным репозиторием необходимо произвести следующие действия:

1. Создать аккаунт на GitHub
2. Создать локальный репозиторий
3. Создать удаленный репозиторий
4. Связать локальный репозиторий с удаленным 

Добавление удаленного репозитория к проекту:
```
git remote add <имя для репозитория>
<url-адрес репозитория в сети>
```

Клонирование внешнего репозитория на локальный ПК:

```
git clone <url-адрес репозитория>
```

Для получения и слияния изменений из удаленного репозитория используется команда `git pull`.

Отправить изменения локального репозитория в удаленный `git push`.