---
title: managed_backup. fn_get_current_xevent_settings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4133f8bb64d5d7e2e2b511c2128b9ddbca1fa550
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67910244"
---
# <a name="managed_backupfn_get_current_xevent_settings-transact-sql"></a>managed_backup. fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого типа расширенного события, поддерживаемого Smart Admin.  
  
 Эта функция используется для возврата или просмотра текущих параметров расширенных событий в целях определения настраиваемых типов событий и текущих конфигураций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
 Эта функция не имеет аргументов.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Каналы администрирования, аналитики и операционные каналы расширенных событий необходимы, включены по умолчанию и не могут быть изменены.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Тип расширенного события|  
|is_configurable|NVARCHAR(128)|Это значение равно **true** , если событие можно настроить, в противном случае — значение **false**.|  
|is_enabled|NVARCHAR(128)|Устанавливается в значение True, если событие включено, и False, если выключено. Для включения событий отладки используйте хранимую процедуру smart_admin.sp_set_parameter.|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуются разрешения **SELECT** на функцию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все расширенные события с их текущим состоянием.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
