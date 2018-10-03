---
Title: 'Tutorial: Using templates in SQL Server Management Studio'
description: Руководство по использованию шаблонов в SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, шаблоны
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: 4d3f2de58bdbfb4f476710bb9bb629dcac3db940
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670042"
---
# <a name="tutorial-using-templates-in-sql-server-management-studio"></a>Руководство. Использование шаблонов в SQL Server Management Studio
Это руководство знакомит вас с готовыми шаблонами Transact-SQL (T-SQL), доступными в среде SQL Server Management Studio (SSMS). Вы узнаете, как выполнять следующие задачи:

> [!div class="checklist"]
> * Создание скриптов T-SQL с помощью обозревателя шаблонов
> * Изменение существующего шаблона 
> * Поиск шаблонов на диске
> * Создание шаблона
   

## <a name="prerequisites"></a>предварительные требования
Для работы с этим руководством требуется среда SQL Server Management Studio и доступ к SQL Server. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

 

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
В следующей статье приведены дополнительные советы и рекомендации по использованию SQL Server Management Studio. 

> [!div class="nextstepaction"]
> [Дополнительные советы и рекомендации по использованию SSMS](ssms-tricks.md)
