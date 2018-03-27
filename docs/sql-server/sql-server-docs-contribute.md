---
title: Участие в работе над документацией по SQL Server | Документы Майкрософт
ms.date: 03/19/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1885c57cfcf21dcdb877fc4c59b229636b74c137
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-contribute-to-sql-server-documentation"></a>Участие в работе над документацией по SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Любой пользователь может принять участие в работе над документацией по SQL Server. В том числе можно исправлять опечатки, предлагать более понятные объяснения и устранять технические неточности. В этой статье описывается, как приступить к работе над материалами и как осуществляется этот процесс.

Существуют два основных процесса работы над документацией:

|||
|---|---|
| [Редактирование в браузере](#githubui) | Подходит для быстрого внесения небольших изменений в любую статью. |
| [Локальное редактирование с помощью средств](#tools) | Подходит для внесения более сложных правок, правок, охватывающих несколько статей, а также в случае частой работы над документацией на сайте docs.microsoft.com. |

## <a id="githubui"></a> Редактирование в браузере

Ниже приводятся общие инструкции по внесению небольших правок в содержимое по SQL Server в браузере. Полностью этот процесс описан в статье [Рабочий процесс для участников GitHub: незначительные или эпизодические изменения](https://docs.microsoft.com/contribute/contribute/light-workflow).

1. В любой статье, в том числе в этой, справа есть кнопка **Изменить**. Найдите статью, которую нужно изменить, и нажмите кнопку **Изменить**, чтобы приступить к работе.

   ![Кнопка "Изменить" для статьи по SQL](./media/sql-server-docs-contribute/edit-sql-server-docs.png)

   Управление всем содержимым на сайте docs.microsoft.com осуществляется в различных репозиториях GitHub. При нажатии кнопки "Изменить" вы переходите к статье в репозитории **sql-docs**. Если вы редактируете статью, посвященную SQL, в документации по Azure, вы переходите в репозиторий **azure-docs**. 

1. Далее щелкните значок карандаша в правом верхнем углу статьи в GitHub.

   ![Кнопка "Изменить"](./media/sql-server-docs-contribute/edit-button.png)

   > [!NOTE]
   > Для редактирования статьи необходимо выполнить вход в GitHub. Если у вас нет учетной записи GitHub, см. статью [Настройка учетной записи GitHub](https://docs.microsoft.com/contribute/contribute/get-started-setup-github). После создания учетной записи GitHub необходимо подтвердить свой адрес электронной почты, прежде чем вы сможете редактировать статьи.

1. Отредактируйте статью в браузере. Все статьи написаны в разметке Markdown. Если вам нужна помощь по работе с Markdown, ознакомьтесь с [основами Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/). Вы также можете посмотреть, как разметка Markdown преобразовывается для просмотра в опубликованных статьях.

1. Прокрутите содержимое страницы вниз до конца окна редактирования, введите название правки и нажмите кнопку **Propose file change** (Предложить изменение файла).

   ![Предложение запроса на вытягивание](./media/sql-server-docs-contribute/propose-file-change.png)

1. На следующей странице щелкните **Create pull request** (Создать запрос на вытягивание).

   ![Создание запроса на вытягивание](./media/sql-server-docs-contribute/create-pull-request.png)

1. Введите название и описание запроса на вытягивание. Затем снова щелкните **Create pull request**.

   ![Создание запроса на вытягивание](./media/sql-server-docs-contribute/create-pull-request2.png)

Дальнейшие указания будут приводиться в комментариях к запросу на вытягивание. Полное описание процесса и дополнительные сведения можно найти в [руководстве для участников](https://docs.microsoft.com/contribute/contribute/light-workflow).

## <a id="tools"></a> Локальное редактирование с помощью средств

Другой способ редактирования заключается в создании вилки репозитория **sql-docs** или **azure-docs** и клонировании его на локальный компьютер. После этого можно использовать редактор Markdown и клиент GIT для отправки изменений. Такой способ подходит для более сложных правок или правок, охватывающих несколько файлов. Он также подходит для участников, часто вносящих изменения в содержимое на сайте docs.microsoft.com.

Сведения об использовании этого метода см. в следующих статьях:

- [Настройка учетной записи GitHub](https://docs.microsoft.com/contribute/contribute/get-started-setup-github)
- [Установка средств для создания содержимого](https://docs.microsoft.com/contribute/contribute/get-started-setup-tools)
- [Локальная настройка репозитория Git для документации](https://docs.microsoft.com/contribute/contribute/get-started-setup-local)
- [Использование средств для внесения изменений](https://docs.microsoft.com/contribute/contribute/full-workflow)

Если вы отправляете запрос на вытягивание со значительными изменениями, вы получите в GitHub комментарий с просьбой отправить **Лицензионное соглашение на участие (CLA)**. Прежде чем ваш запрос на вытягивание будет принят, необходимо заполнить веб-форму.

## <a name="recognition"></a>Распознавание

Если ваши изменения будут приняты, вы будете указаны как участник в верхней части статьи.

![Распознавание участия в работе над содержимым](./media/sql-server-docs-contribute/contribution-recognition.png)

## <a name="sql-docs-overview"></a>Общие сведения о репозитории sql-docs

В этом разделе приводятся дополнительные указания по работе с репозиторием **sql-docs**.

> [!IMPORTANT]
> Сведения в этом разделе относятся к репозиторию **sql-docs**. Если вы редактируете статью, посвященную SQL, в документации по Azure, см. [сведения о репозитории azure-docs в GitHub](https://github.com/MicrosoftDocs/azure-docs/blob/master/README.md).

Содержимое в репозитории [sql-docs](https://github.com/MicrosoftDocs/sql-docs) упорядочивается по нескольким стандартным папкам.

| Папка | Description |
|---|---|
| [docs](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs) | Содержит все опубликованное содержимое по SQL Server. Разделы содержимого логически упорядочиваются по вложенным папкам. |
| [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) | Содержит включаемые файлы. Они представляют собой блоки содержимого, которые могут включаться в несколько статей. |
| **./media** | В каждой папке может быть одна вложенная папка **media** для изображений. Папка **media**, в свою очередь, содержит вложенные папки с именами статей, в которых используются изображения. Изображения должны быть в формате PNG, а их имена должны содержать только символы в нижнем регистре без пробелов. |
| **TOC.MD** | Файл содержания. В каждой вложенной папке может использоваться один файл TOC.MD. |

#### <a name="applies-to-includes"></a>Включаемые файлы applies-to

Каждая статья по SQL Server содержит включаемый файл **applies-to** после заголовка. Он указывает, к каким областям или версиям SQL Server относится статья.

Рассмотрим следующий пример разметки Markdown из включаемого файла **appliesto-ss-asdb-asdw-pdw-md.md**:

```Markdown
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
```

Он добавляет следующий текст в начало статьи:

![Текст области применения](./media/sql-server-docs-contribute/applies-to.png)

Чтобы найти подходящий включаемый файл applies-to для статьи, следуйте приведенным ниже советам.

- Просмотрите другие статьи, посвященные той же функции или связанной задаче. Вы можете начать редактировать эту статью и скопировать разметку Markdown ссылки на включаемый файл applies-to (отменить редактирование можно, не отправляя изменений).
- Выполните поиск файлов, содержащих текст "applies-to", в каталоге [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes). Чтобы быстро отфильтровать файлы, можно использовать кнопку **Find** (Найти) в GitHub. Щелкните файл, чтобы посмотреть, как он преобразовывается для просмотра.
- Обратите внимание на соглашение об именовании. Если в имени есть символы "x", обычно они служат заполнителями, указывающими на то, что служба не поддерживается. Например, **appliesto-xx-xxxx-asdw-xxx-md.md** указывает на то, что поддерживается только хранилище данных SQL Azure, так как поле **asdw** указано, а остальные поля заполнены символами "x".
- В некоторых включаемых файлах указывается номер версии, например **tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md**. Используйте такие включаемые файлы, только если вы знаете, что функция появилась в определенной версии SQL Server. 

## <a name="contributor-resources"></a>Ресурсы для участников

- [Руководство для участников docs.microsoft.com](https://docs.microsoft.com/en-us/contribute/)
- [Руководство по стилю Майкрософт](https://docs.microsoft.com/en-us/teamblog/style-guide)
- [Основы Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

> [!TIP]
> Если вы хотите оставить отзыв по продукту SQL Server, а не по документации, это можно сделать [здесь](https://feedback.azure.com/forums/908035-sql-server).

## <a name="next-steps"></a>Следующие шаги

Изучите [репозиторий sql-docs](https://github.com/MicrosoftDocs/sql-docs) в GitHub.

Найдите статью и отправьте изменение, чтобы помочь сообществу SQL Server. 

Спасибо!


