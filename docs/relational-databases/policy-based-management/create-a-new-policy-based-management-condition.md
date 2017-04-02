---
title: "Создание нового условия управления на основе политик | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Управление на основе политик, создание условий"
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Создание нового условия управления на основе политик
  В этом разделе описывается создание условия управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Для создания условия используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Создание условия  
  
1.  В **обозревателе объектов** щелкните знак "плюс", чтобы развернуть сервер, на котором необходимо создать условие управления на основе политик.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Чтобы развернуть папку **Аспекты** , щелкните знак «плюс».  
  
5.  Щелкните правой кнопкой мыши аспект, в котором требуется создать новое условие, и выберите команду **Создать условие**.  
  
6.  В диалоговом окне **Создание нового условия** в поле **Имя** введите имя нового условия.  
  
7.  Подтвердите правильность аспекта в списке **Аспект** или выберите другой аспект.  
  
8.  Создайте выражения условия в разделе **Выражение**, выбрав свойство аспекта в окне **Поле** , связанный оператор и значение. При добавлении нескольких выражений их можно объединить с помощью операторов **And** или **Or**. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделах [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Общие"](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md), [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Описание"](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md) и [Диалоговое окно "Расширенное редактирование" (условие)](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md).  
  
9. После завершения нажмите кнопку **ОК**.  
  
  