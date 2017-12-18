---
title: "Изменение параметров группы рабочей нагрузки | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18c72fb3a7370f557e9e4dc759234d3ea6ad81f3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="change-workload-group-settings"></a>Изменение параметров группы рабочей нагрузки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Параметры группы рабочей нагрузки можно изменить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Перед началом работы:**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Изменение параметров для группы рабочей нагрузки с использованием следующих средств:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 Можно изменить параметры группы рабочей нагрузки по умолчанию и групп рабочей нагрузки, определяемых пользователем.  
  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 Объем памяти, затрачиваемой на создание индекса в невыровненной секционированной таблице, пропорционален количеству секций, охватываемых индексом. Если общий объем необходимой памяти превышает лимит для каждого запроса (REQUEST_MAX_MEMORY_GRANT_PERCENT), установленный параметром для группы рабочей нагрузки, то создание этого индекса может завершиться ошибкой. Для обеспечения совместимости с версией SQL Server 2005 группа рабочей нагрузки по умолчанию позволяет запросу превысить лимит для каждого запроса с учетом минимального объема памяти, необходимого при запуске, поэтому пользователь может запустить тот же процесс создания индекса в группе рабочей нагрузки по умолчанию, если в пуле ресурсов по умолчанию достаточно памяти, настроенной для выполнения такого запроса.  
  
 Разрешено создание индексов для использования большего объема памяти рабочей области, чем было указано изначально, в целях повышения производительности. Эта специальная обработка поддерживается регулятором ресурсов, однако изначально предоставленная память и любая дополнительная выделенная память ограничены настройками группы рабочей нагрузки и пула ресурсов.  
  
###  <a name="Permissions"></a> разрешения  
 Для изменения параметров группы рабочей нагрузки требуется разрешение CONTROL SERVER.  
  
##  <a name="ChgWGProp"></a> Изменение параметров группы рабочей нагрузки с использованием среды SQL Server Management Studio  
 **Изменение параметров группы рабочей нагрузки с использованием среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В обозревателе объектов рекурсивно разверните узел **Управление** вплоть до и включая папку **Группы рабочей нагрузки** , которая включает группу рабочей нагрузки, подлежащую изменению.  
  
2.  Щелкните правой кнопкой мыши группу рабочей нагрузки, подлежащую изменению, и выберите пункт **Свойства**.  
  
3.  На странице **Свойства регулятора ресурсов** выберите строку для группы рабочей нагрузки в сетке **Группы рабочей нагрузки для пула ресурсов** , если она не выделена автоматически.  
  
4.  Щелкните или дважды щелкните ячейки в строке, подлежащие изменению, и введите новые значения.  
  
5.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="ChgWGTSQL"></a> Изменение параметров группы рабочей нагрузки с использованием Transact-SQL  
 **Изменение параметров группы рабочей нагрузки с использованием Transact-SQL**  
  
1.  Выполните инструкцию ALTER WORKLOAD GROUP, указав значения свойств, которые необходимо изменить.  
  
2.  Выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере изменяется значение параметра максимального объема выделенной памяти в процентах для группы рабочей нагрузки с именем `groupAdhoc`.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Создание группы рабочей нагрузки](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Изменение параметров пула ресурсов](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
