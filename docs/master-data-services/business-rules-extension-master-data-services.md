---
title: Расширение бизнес-правил (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4c18be5f-a3fa-45a8-9be6-0f45f58bbc9e
caps.latest.revision: 16
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e53c611dcbffab854e9b022389afbd3cd4463e66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="business-rules-extension-master-data-services"></a>Расширение бизнес-правил (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

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
|usr|FULL|  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
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
  
  
