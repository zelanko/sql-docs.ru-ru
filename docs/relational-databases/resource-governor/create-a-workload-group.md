---
title: Создание группы рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 237ec09347ab139aabcc9f475f5e3b64aba0f054
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73633002"
---
# <a name="create-a-workload-group"></a>Создание группы рабочей нагрузки

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Группы рабочей нагрузки можно создавать в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Создание группы рабочей нагрузки с использованием:**  [среды SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="LimitationsRestrictions"></a> Ограничения

 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 Объем памяти, затрачиваемой на создание индекса в невыровненной секционированной таблице, пропорционален количеству секций, охватываемых индексом. Если общий объем необходимой памяти превышает лимит для каждого запроса (REQUEST_MAX_MEMORY_GRANT_PERCENT), установленный параметром для группы рабочей нагрузки, то создание этого индекса может завершиться ошибкой. Для обеспечения совместимости с версией SQL Server 2005 группа рабочей нагрузки по умолчанию позволяет запросу превысить лимит для каждого запроса с учетом минимального объема памяти, необходимого при запуске, поэтому пользователь может запустить тот же процесс создания индекса в группе рабочей нагрузки по умолчанию, если в пуле ресурсов по умолчанию достаточно памяти, настроенной для выполнения такого запроса.  
  
 Разрешено создание индексов для использования большего объема памяти рабочей области, чем было указано изначально, в целях повышения производительности. Эта специальная обработка поддерживается регулятором ресурсов, однако изначально предоставленная память и любая дополнительная выделенная память ограничены настройками группы рабочей нагрузки и пула ресурсов.  
  
###  <a name="Permissions"></a> Permissions

 Для создания группы рабочей нагрузки требуется разрешение CONTROL SERVER.  
  
##  <a name="CreRPProp"></a> Создание группы рабочей нагрузки в среде SQL Server Management Studio

 **Создание группы рабочей нагрузки с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В обозревателе объектов рекурсивно разверните узел **Управление** вплоть до узла «Пул ресурсов», содержащего группу рабочей нагрузки, которую необходимо изменить.  
  
2.  Щелкните правой кнопкой мыши папку **Группы рабочей нагрузки** и выберите команду **Создать группу рабочей нагрузки**.  
  
3.  Убедитесь в том, что в сетке **Пулы ресурсов** выделен подсветкой пул ресурсов, в который должна быть добавлена группа рабочей нагрузки.  
  
4.  В сетке **Группы рабочей нагрузки для пула ресурсов** будет присутствовать новая строка с пустым именем и значениями по умолчанию в других столбцах.  
  
5.  Щелкните ячейку **Имя** и введите имя для группы рабочей нагрузки.  
  
6.  Щелкните или дважды щелкните все прочие ячейки в строке, для которых необходимо задать параметры, отличные от применяемых по умолчанию, и введите новые значения.  
  
7.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  

##  <a name="CreRPTSQL"></a> Создание группы рабочей нагрузки с помощью Transact-SQL  
 **Создание группы рабочей нагрузки с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Выполните инструкцию CREATE WORKLOAD GROUP, указав значения свойств, которые необходимо установить.  
  
2.  Выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)

 В следующем примере создается группа рабочей нагрузки с именем `groupAdhoc` , которая находится в пуле ресурсов с именем `poolAdhoc`.  
  
```sql
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:

 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Изменение параметров группы рабочей нагрузки](../../relational-databases/resource-governor/change-workload-group-settings.md)   
 [Создание и проверка определяемой пользователем функции-классификатора](../../relational-databases/resource-governor/create-and-test-a-classifier-user-defined-function.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)  
  
  
