---
title: managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 26fc0678d8597cc8a56211e829bdc598c734f168
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38029539"
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого типа расширенного события, поддерживаемого Smart Admin.  
  
 Эта функция используется для возврата или просмотра текущих параметров расширенных событий в целях определения настраиваемых типов событий и текущих конфигураций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Аргументы  
 Эта функция не имеет аргументов.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Каналы администрирования, аналитики и операционные каналы расширенных событий необходимы, включены по умолчанию и не могут быть изменены.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Тип расширенного события|  
|is_configurable|NVARCHAR(128)|Это имеет значение **True** Если событие можно настроить, в противном случае ему присвоено **False**.|  
|is_enabled|NVARCHAR(128)|Устанавливается в значение True, если событие включено, и False, если выключено. Для включения событий отладки используйте хранимую процедуру smart_admin.sp_set_parameter.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется **ВЫБЕРИТЕ** разрешений на функцию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все расширенные события с их текущим состоянием.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
