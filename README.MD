[![Python 2.7.7](https://img.shields.io/badge/python-2.7.7-blue.svg)](https://www.python.org/download/releases/2.7.7/)
[![Build status](https://travis-ci.org/SerVB/TheRecentStatOfYou.svg?master)](https://travis-ci.org/SerVB/TheRecentStatOfYou)

# Русский [read in English](#English)

# The Recent Stat of You
Мод с открытым исходным кодом для отображения недавней статистики игроков в бою.

## Суть
Главное отличие этого мода от аналогичных &mdash; это возможность отображения обещающего быть более информативным **недавнего** рейтинга эффективности (примерно за последнюю тысячу боев, то есть примерно за последние 50 часов игрового времени). В остальном это всe тот же мод, который Вы видели у *XVM*, *PolarFox* и *Ekspoint*.

Мод позволяет отображать недавнюю статистику игроков в следующих местах:
- В окне загрузки боя.
- В ушах.
- В маркерах над техникой.
- В таблице игроков при нажатии Tab.

## Как это выглядит
На данный момент показ статистики достигается переименованием игроков: к имени добавляется префикс. Префикс настраивается в файле конфигурации.

## Как это работает
Мод обращается к провайдерам недавней статистики, и если она находится, выводит ее заместо общей статистики.

Данные берутся с сайтов [kttc.ru](https://kttc.ru/) (разрешение на использование от представителя сайта получено) и [noobmeter.com](https://noobmeter.com/) (связаться с представителем сайта не удалось, поэтому пока считаем, что запрета на использование сайта нет).

## Внести вклад
Открытие Pull Request'ов, решающих как планируемые задачи, так и любые другие, приветствуется. Любые идеи по развитию также с радостью будут услышаны, Вы можете оставить свои вопросы и предложения во вкладке "[Issues](https://github.com/SerVB/TheRecentStatOfYou/issues)".

В ближайшее время я улучшать мод не планирую, ведь у меня есть другие проекты. Сам использую мод в текущем состоянии, и это меня устраивает.

## Далекие планы
во вкладке "[Issues](https://github.com/SerVB/TheRecentStatOfYou/issues)".

## Скриншоты и скачивание
во вкладке "[Releases](https://github.com/SerVB/TheRecentStatOfYou/releases)".

## Установка
Положите файл `.wotmod` в папку `mods/{версия_игры}/`. Для смены стандартных настроек мода скачайте папку `configs` и положите ее в папку `mods/`.

## Построение из исходников
Запустите файл `build.py` (рекомендуется версия Питона 2.7.7), исходники соберутся в папке `build/`.

## Известные проблемы
- При начале загрузки боя происходит подвисание от трех до десяти секунд, связанное со скачиванием данных с сайта. Запросы происходят многопоточно, асинхронно и одновременно, поэтому тут вряд ли можно что-то улучшить. Даже если найдется способ получать статистику всех игроков в бою за один запрос, он будет проходить за то же время...
- Клиент иногда пишет в лог, что не может найти ник игрока и поэтому использует более медленный вариант поиска. Наверное, это связано с тем, что мод фактически переименовывает игроков. Пока видимых симптомов в клиенте игры не замечено. Но с обновлением клиента это может стать причиной вылетов, если не полной неработоспособности...

## FAQ
**Q**. Новая версия Танков, а мод не адаптирован. Автор признаков жизни не подает. Моду конец?  
**A**. Посмотрите файлы, изменяемые модом, в файле `mod_recent_stat_init.py`. Найдите те же файлы в репозитории декомпилированных файлов танкового клиента [WorldOfTanks-Decompiled](https://github.com/StranikS-Scan/WorldOfTanks-Decompiled/). Если они не менялись с новым патчем, то мод скорее всего будет работать в новой версии, необходимо только переложить его в папку с номером новой версии (по крайней мере, при обновлении с 1.1 на 1.2 код мода модифицировать не пришлось).

**Q**. На каком кластере работает мод?  
**A**. Мод должен работать на любых кластерах. Попробуйте поменять регион в конфиге `config_main.json`.

**Q**. Как поменять провайдера недавней статистики или полностью отключить возможность показа недавней статы?  
**A**. В конфиге `config_main.json`.

## Благодарности
- **VasyaPRO_2014** &mdash; идея создания мода статистики в бою с открытым исходным кодом; система сборки мода ([тема на Korean Random](https://koreanrandom.com/forum/topic/29691-09152-%D1%81%D1%82%D0%B0%D1%82%D0%B8%D1%81%D1%82%D0%B8%D0%BA%D0%B0-%D0%B8%D0%B3%D1%80%D0%BE%D0%BA%D0%BE%D0%B2-%D0%B2-%D0%B1%D0%BE%D1%8E-%D0%B1%D0%B5%D0%B7-xvm/), [репозиторий на GitHub](https://github.com/VasyaPRO/StatsInBattle)).
- Проект [WorldOfTanks-Decompiled](https://github.com/StranikS-Scan/WorldOfTanks-Decompiled/) &mdash; декомпилированные файлы танкового клиента использовались для создания мода.
- Сайты [kttc.ru](https://kttc.ru/) и [noobmeter.com](http://noobmeter.com/) &mdash; провайдеры недавней статистики игроков.
- [Гайд](https://koreanrandom.com/forum/topic/36987-mod-packages-%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D1%8B-%D0%BC%D0%BE%D0%B4%D0%BE%D0%B2/) по созданию `.wotmod` пакетов.
- **Ekspoint** помогал по многим вопросам. 
- [Люди](https://github.com/SerVB/TheRecentStatOfYou/graphs/contributors), которые контрибьютили непосредственно в проект.

# English

# The Recent Stat of You
An open-source mod displaying players' recent statistics in battle.

## Idea
The main difference of this mod from similar is the ability to display more informative **recent** efficiency rating (approximately of the last thousand battles, that is, of the last 50 hours of playing time). Otherwise, this is the same mod that you saw from *XVM*, *PolarFox* and *Ekspoint*.

The mod allows to display statistics in the following places:
- On the battle loading screen.
- On the battle players panel.
- In markers.
- On the Tab players panel.

## How does it look like?
Currently, statistics are displayed using players renaming: a prefix is added to the name. The prefix can be configured in the configuration file.

## How does it work?
Mod asks the providers of recent statistics, and there is an answer, displays recent stats instead of overall statistics.

Data is taken from [kttc.ru](https://kttc.ru/) (permission is granted) и [noobmeter.com](https://noobmeter.com/) (I couldn't contact the site developers so I assume there is no prohibition to use the site).

## Contribute
Pull request opening to resolve planning tasks or any other tasks is appreciated.
Any ideas on development will also be happy to be heard, you can leave your questions and suggestions in the "[Issues](https://github.com/SerVB/TheRecentStatOfYou/issues)" tab.

In the near future, I do not plan to improve the mod, because I have other projects. I myself use the mod in the current state, and it suits me.

## Planing tasks
are located in the "[Issues](https://github.com/SerVB/TheRecentStatOfYou/issues)" tab.

## Screenshots and downloads
are located in the "[Releases](https://github.com/SerVB/TheRecentStatOfYou/releases)" tab.

## Installation
Place the file `.wotmod` into `mods/{game_version}/`. To change default mod settings download the dir `configs` and place it into `mods/`.

## Build from sources
Run the file `build.py` (I recommend Python 2.7.7), sources will be built in the dir `build/`.

## Known issues
- At a battle loading start there is a lag of 3-10 seconds. It's because of data downloading from the Internet. Downloading happens in multiple threads, asynchronously and simultaneously so I think there is nothing to improve. It's the time of a single query completion.
- Sometimes there are messages in the log like "can't find player name, use slow search". Maybe it's because the mod just renames players. There is no symptoms have been noticed. Anyway, in future game versions it can became a problem...

## FAQ
**Q**. The mod isn't adopted for a new World of Tanks version.
**A**. Check `mod_recent_stat_init.py` for the list of modified files. Find the same files in game decompiled sources [WorldOfTanks-Decompiled](https://github.com/StranikS-Scan/WorldOfTanks-Decompiled/). If they haven't been changed, it's likely the mod will work. It's only needed to put the mod in the new dir. For example, the mod was working after update from 1.1 to 1.2.

**Q**. Which clusters are supported?  
**A**. All clusters should be supported. Try to change it in `config_main.json`.

**Q**. How to change providers of recent stat or completely disable the recent stat feature?  
**A**. In `config_main.json`.

## Attributions
- **VasyaPRO_2014** &mdash; idea of open-source mod showing statistics in battle; mod builder ([topic at Korean Random](https://koreanrandom.com/forum/topic/29691-09152-%D1%81%D1%82%D0%B0%D1%82%D0%B8%D1%81%D1%82%D0%B8%D0%BA%D0%B0-%D0%B8%D0%B3%D1%80%D0%BE%D0%BA%D0%BE%D0%B2-%D0%B2-%D0%B1%D0%BE%D1%8E-%D0%B1%D0%B5%D0%B7-xvm/), [GitHub repo](https://github.com/VasyaPRO/StatsInBattle)).
- [WorldOfTanks-Decompiled](https://github.com/StranikS-Scan/WorldOfTanks-Decompiled/) Project &mdash; decompiled files have been used to develop the modification.
- Sites [kttc.ru](https://kttc.ru/) и [noobmeter.com](http://noobmeter.com/) &mdash; recent stats providers.
- [Guide](https://koreanrandom.com/forum/topic/36987-mod-packages-%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D1%8B-%D0%BC%D0%BE%D0%B4%D0%BE%D0%B2/) of `.wotmod` packages creation.
- **Ekspoint** helped in many questions. 
- [People](https://github.com/SerVB/TheRecentStatOfYou/graphs/contributors) who contribute into the project.
