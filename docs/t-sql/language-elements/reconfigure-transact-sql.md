---
title: "RECONFIGURE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/20/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RECONFIGURE
- RECONFIGURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- reconfiguring configuration options
- configuration options [SQL Server], reconfiguring
- updating configuration options
- RECONFIGURE, RECONFIGURE statement
- RECONFIGURE
- RECONFIGURE, WITH OVERRIDE statement
ms.assetid: 2e6e4eeb-b70b-4f45-a253-28ac4e595d75
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32039a4077f028a078e9265c6d18f5cbb6187e3f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="reconfigure-transact-sql"></a>RECONFIGURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет текущее настроенное значение ( **config_value** столбца в **sp_configure** результирующего набора) параметра конфигурации изменен с **sp_configure** системы Хранимая процедура. Поскольку некоторые параметры конфигурации требуется остановка и перезапуск сервера для обновления текущее значение этого параметра, инструкция RECONFIGURE не всегда обновляет текущее значение ( **run_value** столбца в **хранимой процедуры sp_configure**  результирующего набора) для измененного параметра конфигурации.    
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Синтаксис    
    
```    
    
RECONFIGURE [ WITH OVERRIDE ]    
```    
    
## <a name="arguments"></a>Аргументы    
 RECONFIGURE    
 Указывает, что если для изменения параметра конфигурации не требуется остановка и перезапуск сервера, то значение будет изменено. Инструкция RECONFIGURE также проверяет новые конфигурационные значения либо значения, которые не являются допустимым (например, значение порядка сортировки, которые отсутствуют в **syscharsets**) или выявляет нежелательные значения. Для параметров конфигурации, которые можно изменять без остановки или перезапуска сервера, текущие значения параметров должны совпасть с новыми после вызова RECONFIGURE.    
    
 WITH OVERRIDE    
 Отключает проверку значения конфигурации (на недопустимые или нежелательные значения) поиск **интервал восстановления** дополнительный параметр конфигурации.    
    
 Практически с любого параметра конфигурации можно перенастроить с помощью параметра WITH OVERRIDE, однако некоторые неустранимые ошибки по-прежнему не могут. Например **параметре min server memory** параметр конфигурации не может быть настроен значение больше значения, указанного в **Макс. памяти сервера** параметра конфигурации.
      
## <a name="remarks"></a>Замечания    
 **sp_configure** не принимает новые значения параметров конфигурации вне документированные допустимых диапазонов для каждого параметра конфигурации.    
    
 Недопустимо использование RECONFIGURE в явной или неявной транзакции. При одновременной перенастройке нескольких параметров в случае сбоя какой-либо из операций перенастройки ни одна из этих операций не вступит в силу.    
    
 При перенастройке регулятора ресурсов, в описании RECONFIGURE параметра [ALTER RESOURCE GOVERNOR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-resource-governor-transact-sql.md).    
    
## <a name="permissions"></a>Permissions    
 Разрешения для RECONFIGURE по умолчанию предоставляются участникам, которым предоставлено разрешение ALTER SETTINGS. **Sysadmin** и **serveradmin** этим разрешением неявно обладают предопределенных ролей сервера.    
    
## <a name="examples"></a>Примеры    
 Следующий пример устанавливает верхний предел для параметра `recovery interval` в `75` минут с помощью разрешения `RECONFIGURE WITH OVERRIDE`. Интервалы восстановления более 60 минут нежелательны и по умолчанию запрещены. Однако из-за параметра `WITH OVERRIDE` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не проверяет, является ли указанное значение (`90`) параметра `recovery interval` допустимым.    
    
```    
EXEC sp_configure 'recovery interval', 75'    
RECONFIGURE WITH OVERRIDE;    
GO    
```    
    
## <a name="see-also"></a>См. также:    
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)     
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)    
    
  

