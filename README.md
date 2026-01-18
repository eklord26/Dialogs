# Проект Dialogs
Проект создаётся в целях сократить время на разработку модуля Диалогов для внутренней разработки NightFactory.

## Описание реализации модуля:
В модуле диалогов представлено несколько сущностей, которые реализованы в качестве ScriptableObjects и хранят информацию по диалогам персонажей в игре:
* Dialog
* Character

Было решено всё таки вынести отдельных персонажей, потому что разделение по фразам и заполнению этих фраз займёт намного больше времени.

Рассмотрим подробнее структуру классов данных:
1. __Phrase__
   * Index        - Порядковый номер в диалоге
   * Character    - Имя персонажа для поиска через Linq в ___Dialog___
   * Value        - Текст фразы персонажа
     
2. __Character__
   * Name         - Имя персонажа
   * Description  - Описание персонажа (Может использоваться для титулов и размещения доп инфы о персонаже)
   * ImagePath    - Путь к изображению персонажа
     
3. __Dialog__
   * Phrases[]    - Массив всех фраз диалога
   * Characters[] - Массив всех персонажей, участвующих в диалогах
   * Status       - Статус завершения диалога. Имеет значения, указанные в ___DialogStatus___

## Описание файловой структуры модуля Диалогов:

```diff
$   Dialogs/
!   ├── Scripts/
$   │   ├── Base/
$   │   │   ├── Interface/
#   │   │   │   ├── IDialog.cs
#   │   │   │   ├── IDialogRepository.cs
#   │   │   │   └── IDialogManager.cs
$   │   │   ├── Enum/
#   │   │   │   └── DialogStatus.cs
$   │   │   ├── EventBus/
#   │   │   │   └── DialogEventBus.cs
$   │   ├── Managers/
#   │   │   └── DialogManager.cs
$   │   └── Models/
#   │   │   ├── DialogRepository.cs
$   │   │   ├── Script/
#   │   │   │   └── DialogScript.cs
$   │   │   └── Data/
#   │   │       ├── Character.cs - ScriptableObjects
#   │   │       ├── Dialog.cs    - ScriptableObjects
#   │   │       └── Phrase.cs
$   ├── Scenes/
+   │   └── TestModule/
#   │   │   ├── TestCommonDialog.scene - Сцена с проверкой базовых диалогов
#   │   │   └── TestManyAnswers.scene  - Сцена с проверкой диалогов с выбором ответа
$   ├── Resources/
+   │   ├── Characters/
#   │   │   ├── Chatacter_man.asset
#   │   │   ├── Chatacter_man_angry.asset
#   │   │   ├── Chatacter_woman.asset
#   │   │   └── Chatacter_woman_scary.asset
+   │   └── Dialogs/
#   │   │   ├── DialogScriptable_0.asset
#   │   │   ├── DialogScriptable_1.asset
#   │   │   └── DialogScriptable_2.asset

Легенда:
! Основная реализация
# Файлы проекта
+ Директории конкретных реализаций (Scenes, Prefabs, ScriptableObjects)
```
___
### Автор: Eklord
### Версия Unity: 6000.0.58f2
### Дата составления модуля: WIN
