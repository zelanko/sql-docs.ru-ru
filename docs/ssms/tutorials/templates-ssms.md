---
Title: 'Tutorial: Using Templates in SQL Server Management Studio'
description: Учебник по использованию шаблонов в среде SSMS. , и делает это по-другому.
keywords: SQL Server, SSMS, SQL Server Management Studio, шаблоны
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
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
ms.openlocfilehash: a01586f4ab3d002e33b7679f6fe2e5a165f260e1
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-using-templates-within-sql-server-management-studio"></a>Учебник. Использование шаблонов в среде SQL Server Management Studio
В этом учебнике приводятся основные сведения о готовых шаблонах Transact-SQL (T-SQL), доступных в среде SQL Server Management Studio (SSMS). Вы узнаете, как выполнять следующие задачи:

> [!div class="checklist"]
> * создавать скрипты T-SQL с помощью обозревателя шаблонов;
> * изменять существующий шаблон; 
> * находить шаблоны на диске;
> * Создание шаблона
   

## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio и доступ к SQL Server. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).

 

## <a name="using-the-template-browser"></a>Использование обозревателя шаблонов
В этом разделе вы научитесь находить и использовать **обозреватель шаблонов**. 

1. Запустите SQL Server Management Studio.
2. В меню **Вид** выберите пункт **Обозреватель шаблонов** (CTRL+ALT+T). 

    ![Обозреватель шаблонов](media/templates-ssms/templatebrowser.png)
    - В нижней части **обозревателя шаблонов** можно просмотреть недавно использовавшиеся шаблоны.

3. Разверните нужный узел, щелкните шаблон правой кнопкой мыши и выберите пункт "Открыть".

    ![Открытие шаблона](media/templates-ssms/opentemplate.png)
    - Тот же самый результат будет, если дважды щелкнуть шаблон.

4. Откроется новое окно запроса с уже заполненным кодом T-SQL. 
5. Измените шаблон в соответствии со своими потребностями, а затем **выполните** запрос.
    
    ![Создание шаблона базы данных](media/templates-ssms/createdbtemplate.png)


## <a name="edit-an-existing-template"></a>Изменение существующего шаблона
В **обозревателе шаблонов** можно также изменять существующие шаблоны.  

1. Найдите нужный шаблон в **обозревателе шаблонов**.
2. Щелкните шаблон правой кнопкой мыши и выберите пункт **Изменить**.

    ![Изменение шаблона](media/templates-ssms/edittemplate.png)

3. В открывшемся окне запроса внесите необходимые изменения.
4. Сохраните шаблон, выбрав **Файл** > **Сохранить** (CTRL+S).
5. Закройте окно запроса.
6. Повторно откройте сохраненный шаблон. Он должен содержать внесенные изменения.
 

## <a name="locate-the-templates-on-disk"></a>Поиск шаблонов на диске
Открыв шаблон, можно найти его на диске.

1. Выберите шаблон в **обозревателе шаблонов**, а затем выберите команду **Изменить**.
2. Щелкните правой кнопкой мыши **заголовок запроса** и выберите пункт **Открыть содержащую папку**. В проводнике должна открыться папка на диске с шаблонами. 

    ![Шаблоны на диске](media/templates-ssms/templatesondisk.png)
  

## <a name="create-a-new-template"></a>Создание шаблона
В **обозревателе шаблонов** также есть возможность создавать шаблоны. Ниже приведены инструкции по созданию папки и последующему созданию шаблона в ней. Однако таким образом можно также создавать пользовательские шаблоны в существующих папках. 

1. Откройте **обозреватель шаблонов**.
2. Щелкните правой кнопкой мыши узел "Шаблоны SQL Server" и выберите пункты **Создать** > **Папка**.
3. Назовите папку **Пользовательские шаблоны**.

    ![Создание пользовательских шаблонов](media/templates-ssms/creatingcustomtemplate.png)

4. Щелкните правой кнопкой мыши созданную папку **Пользовательские шаблоны**, выберите пункты **Создать** > **Шаблон** и введите имя шаблона.
 
    ![Создание пользовательского шаблона](media/templates-ssms/createnewtemplate.png)
   
5. Щелкните правой кнопкой мыши созданный шаблон и выберите пункт **Изменить**. Откроется **новое окно запроса**.
6. Введите текст T-SQL, который нужно сохранить. 
7. Сохраните файл, выбрав в меню **Файл** команду **Сохранить**.
8. Закройте **окно запроса** и откройте новый пользовательский шаблон. 

    

## <a name="next-steps"></a>Следующие шаги
В следующей статье приводятся некоторые дополнительные советы и рекомендации по использованию SQL Server Management Studio. 

Перейдите к следующей статье, чтобы узнать больше
> [!div class="nextstepaction"]
> [Кнопка дальнейших действий](ssms-tricks.md)
