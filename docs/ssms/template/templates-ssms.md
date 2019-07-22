---
title: Использование шаблонов в среде SQL Server Management Studio
description: Руководство по использованию шаблонов в SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, шаблоны
author: MashaMSFT
ms.author: mathoma
ms.topic: tutorial
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
helpviewer_keywords:
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.custom: ''
ms.date: 03/13/2018
ms.openlocfilehash: b3df46f3536c488ff863287a0efb26ed7063ffc2
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266649"
---
# <a name="use-templates-in-sql-server-management-studio"></a>Использование шаблонов в SQL Server Management Studio

Это руководство знакомит вас с готовыми шаблонами Transact-SQL (T-SQL), доступными в среде SQL Server Management Studio (SSMS). Вы узнаете, как выполнять следующие задачи:

## <a name="prerequisites"></a>предварительные требования

Для работы с этим руководством требуется среда SQL Server Management Studio и доступ к SQL Server.

* Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

* Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

## <a name="use-template-browser"></a>Использование обозревателя шаблонов

В этом разделе вы научитесь находить и использовать обозреватель шаблонов.

1. Откройте среду SQL Server Management Studio.

2. В меню **Вид** выберите пункт **Обозреватель шаблонов** (CTRL+ALT+T):

    ![Открытие обозревателя шаблонов](media/templates-ssms/templatebrowser.png)

    В нижней части обозревателя шаблонов находятся недавно использовавшиеся шаблоны.

3. Разверните интересующий вас узел. Щелкните шаблон правой кнопкой мыши и выберите **Открыть**:

    ![Открытие шаблона](media/templates-ssms/opentemplate.png)

    Вы также можете открыть шаблон, дважды щелкнув его имя.

4. Откроется новое окно запроса. Скрипт T-SQL будет уже заполнен.

5. Измените шаблон в соответствии с вашими требованиями и выберите **Выполнить**, чтобы запустить запрос:

    ![Создание шаблона базы данных](media/templates-ssms/createdbtemplate.png)

## <a name="edit-an-existing-template"></a>Изменение существующего шаблона

Обозреватель шаблонов также позволяет вам редактировать уже существующие шаблоны.  

1. Для этого перейдите к нужному вам шаблону в обозревателе.

2. Щелкните шаблон правой кнопкой мыши и выберите **Изменить**:

    ![Изменение шаблона](media/templates-ssms/edittemplate.png)

3. В открывшемся окне запроса внесите нужные изменения.

4. Чтобы сохранить шаблон, выберите **Файл** > **Сохранить** (CTRL+S).

5. Закройте окно запроса.

6. Повторно откройте шаблон. В нем должны появиться ваши изменения.

## <a name="locate-templates-on-disk"></a>Поиск шаблонов на диске

Когда у вас открыт шаблон, вы можете просматривать шаблоны, находящиеся на диске.

1. В обозревателе шаблонов выберите шаблон и нажмите **Изменить**.

2. Правой кнопкой мыши щелкните **Заголовок запроса** и выберите **Открыть содержащую папку**. Обозреватель откроет папку диска, где хранятся шаблоны: 

   ![Шаблоны на диске](media/templates-ssms/templatesondisk.png)
  
## <a name="create-a-new-template"></a>Создание шаблона

В обозревателе шаблонов вы также можете создавать шаблон. Ниже приведены инструкции по созданию папки и созданию нового шаблона внутри нее. Они также позволят вам создать настраиваемый шаблон в существующей папке. 

1. Откройте обозреватель шаблонов.

2. Щелкните правой кнопкой мыши узел **Шаблоны SQL Server** и выберите пункты **Создать** > **Папка**.

3. Назовите папку **Пользовательские шаблоны**.

    ![Создание папки для настраиваемых шаблонов](media/templates-ssms/creatingcustomtemplate.png)

4. Щелкните правой кнопкой мыши созданную папку "Настраиваемые шаблоны" и выберите пункты **Создать** > **Шаблон**. Введите имя шаблона:

    ![Создание настраиваемого шаблона](media/templates-ssms/createnewtemplate.png)

5. Щелкните правой кнопкой мыши созданный шаблон и выберите **Изменить**. Откроется новое окно запроса.

6. Введите текст T-SQL, который вы хотите сохранить.

7. В меню **Файл** выберите пункт **Сохранить**.

8. Закройте окно запроса и откройте свой новый настраиваемый шаблон.

## <a name="next-steps"></a>Следующие шаги

Лучший способ познакомиться с SSMS — это поработать в среде самостоятельно. Эти *руководства* и *статьи* помогут вам ознакомиться с различными функциями SSMS.  С их помощью вы научитесь работать с компонентами SSMS и легко находить регулярно используемые функции.

* [Подключение к экземпляру и отправка запросов к нему](../tutorials/connect-query-sql-server.md)
* [Создание скриптов](../tutorials/scripting-ssms.md)
* [Конфигурация SSMS](../tutorials/ssms-configuration.md)
* [Дополнительные советы и рекомендации по использованию SSMS](../tutorials/ssms-tricks.md)