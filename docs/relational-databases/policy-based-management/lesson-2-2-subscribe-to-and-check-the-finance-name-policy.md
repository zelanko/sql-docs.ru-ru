---
title: "Подписка на политику имен базы данных Finance и проверка обновлений | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c8ead370baae4066fecdc6545636668958991adf
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-2---subscribe-to-and-check-the-finance-name-policy"></a>Урок 2.2. Подписка на политику имен базы данных Finance и проверка обновлений
В этой задаче будет произведена настройка по подписке базы данных Finance к категории политики финансов. Затем будет протестирована политика имен финансов.  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a>Подписка на категорию политик «Finance»  
  
1.  В обозревателе объектов разверните узел **Базы данных**, щелкните правой кнопкой мыши **Finance**, наведите указатель на пункт **Политики**и выберите пункт **Категории**.  
  
2.  Установите флажок **Есть подписка** для категории **Finance** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a>Тестирование принудительного применения политики имен финансов  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте окно запроса. Выполните приведенные ниже инструкции, которые попытаются создать таблицу, нарушающую политику **Имена финансов** . Таблица нарушает политику, так как ее имя не начинается с букв **fintbl**.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    Обратите внимание, что политика предотвращает создание таблицы и возвращает информационное сообщение, содержащее имя политики.  
  
2.  Для предоставления достоверного имени измените код, как указано ниже, и снова запустите инструкцию.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    В это время создается таблица.  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a>Применение политики ко всему серверу  
  
1.  В данный момент на категорию политики финансов подписана только база данных Finance. В большинстве случаев легче применить категорию политики ко всему серверу. В обозревателе объектов разверните узел **Управление**, щелкните правой кнопкой мыши узел **Управление политиками**и выберите пункт **Управление категориями**.  
  
2.  Найдите категорию Finance в диалоговом окне **Управление категориями политик** и установите флажок **Сделать подписки базы данных обязательными** для категории Finance.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Теперь категория Finance применяется ко всем базам данных, но созданное условие ограничивает политику имен финансов для базы данных Finance. Это показывает то, как используются сложные сочетания условий для целевых политик для их правильного применения к нескольким серверам.  
  
## <a name="summary"></a>Сводка  
В этом учебнике показано создание условий управления на основе политик, политик и групп политик, а также применение фильтров и проверка соответствия целей управления на основе политик.  
  
## <a name="next"></a>Дальше  
Данный учебник завершен. Чтобы вернуться к началу, щелкните ссылку [Учебник. Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Список учебников см. в разделе [Учебные материалы по SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## <a name="see-also"></a>См. также:  
[Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
  

