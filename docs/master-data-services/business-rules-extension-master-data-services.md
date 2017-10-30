---
title: "Расширение бизнес-правил (службы Master Data Services) | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c18be5f-a3fa-45a8-9be6-0f45f58bbc9e
caps.latest.revision: 16
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: e83f09094cde9a2643913fceae32d1f6a07a7c09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="business-rules-extension-master-data-services"></a>Расширение бизнес-правил (Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]вы можете применять пользовательские скрипты SQL в качестве расширения предопределенных условий и действий.  
  
> [!NOTE]  
>  Все сценарии должны быть определены по схеме [usr].  
  
 В качестве условия бизнес-правила можно использовать функции SQL, которые удовлетворяют следующим критериям.  
  
-   Тип возвращаемого значения должен быть BIT.  
  
-   Для типов параметров поддерживаются только следующие типы.  
  
    -   NVARCHAR  
  
    -   DATETIME2  
  
    -   DECIMAL (точность, масштаб)  
  
         точность должна быть равна 38  
  
         масштаб должен иметь значение от 0 до 7  
  
 Хранимые процедуры SQL, использующие следующий синтаксис, можно использовать в качестве действия бизнес-правила.  
  
```  
CREATE PROCEDURE [usr].[YourAction]  
       (         
            @MemberIdList mdm.[MemberId] READONLY,  
            @ModelName NVARCHAR(MAX),  
            @VersionName NVARCHAR(MAX),  
            @EntityName NVARCHAR(MAX),  
            @BusinessRuleName NVARCHAR(MAX)  
        )    
      AS BEGIN    
       ...     
       END  
  
```  
  
 Пользовательские сценарии не будут добавляться в пакеты развертывания. Перед развертыванием пакета убедитесь, что целевая база данных Master Data Services содержит все сценарии, которые используются в бизнес-правилах.  
  
 Действия сценариев будут выполняться как mds_br_user со следующими разрешениями.  
  
|||  
|-|-|  
|**Схема**|**Permissions**|  
|mdm|SELECT|  
|stg|SELECT, UPDATE, DELETE, EXECUTE, INSERT|  
|usr|ПОЛНОЕ|  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Иметь разрешение на доступ к функциональной области "Администрирование системы".  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Пользовательские сценарии были добавлены в базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="create-a-business-rule-to-take-a-user-defined-script-as-a-condition-or-as-an-action"></a>Создание бизнес-правила для использования пользовательского сценария как условия или действия  
  
1.  В диспетчере основных данных щелкните **Системное администрирование**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** выберите модель из раскрывающегося списка **Модель** .  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Нажмите кнопку **Добавить**.  
  
7.  Выполните следующие действия, чтобы создать пользовательский сценарий как условие.  
  
    1.  В разделе **If** нажмите кнопку **Добавить** . Отобразится панель.  
  
    2.  Из раскрывающегося списка **Оператор** в области **Пользовательский скрипт** выберите пользовательскую функцию.  
  
    3.  Отобразятся все параметры пользовательской функции.  
  
    4.  Присвойте значения всем параметрам  
  
    5.  Нажмите кнопку **Сохранить**.  
  
8.  Выполните следующие шаги, чтобы использовать пользовательский сценарий как действие.  
  
    1.  В разделе **Then** нажмите кнопку **Добавить** . Отобразится панель.  
  
    2.  Из раскрывающегося списка **Оператор** в области **Пользовательский скрипт** выберите пользовательскую функцию.  
  
    3.  Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)   
 [Условия бизнес-правил (службы Master Data Services)](../master-data-services/business-rule-conditions-master-data-services.md)   
 [Действия бизнес-правил (службы Master Data Services)](../master-data-services/business-rule-actions-master-data-services.md)  
  
  

