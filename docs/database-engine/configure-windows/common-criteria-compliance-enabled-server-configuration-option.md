---
title: "Параметр конфигурации сервера \"common criteria compliance enabled\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd939e4293699ce458307bf70c1bb5fa4ac90e7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a>Параметр конфигурации сервера «common criteria compliance enabled»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Параметр common criteria compliance enabled включает следующие элементы, необходимые для поддержки стандарта Common Criteria.  
  
|Критерии|Описание|  
|--------------|-----------------|  
|Защита остаточных данных (RIP)|Критерий RIP требует, чтобы выделяемая память была перезаписана известным битовым шаблоном, прежде чем она будет перераспределена для другого ресурса. Соответствие стандарту RIP может повысить безопасность, однако может привести к снижению производительности. После включения параметра common criteria compliance enabled производится перезапись памяти.|  
|Возможность просматривать статистику имени входа|После включения параметра common criteria compliance enabled включается аудит входа. Каждый раз, когда пользователь успешно входит в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], становятся доступными сведения о времени последнего успешного входа, времени последней неудачной попытки входа и о количестве попыток между последним успешным уходом и текущим входом. Чтобы увидеть статистику входа, запросите динамическое административное представление [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md) .|  
|Разрешение `GRANT` на столбец не переопределяет запрет `DENY` на таблицу|После включения параметра common criteria compliance enabled запрет `DENY` на уровне таблицы имеет больший приоритет, чем разрешение `GRANT` на уровне столбца. Если этот параметр выключен, разрешение `GRANT` на столбец имеет больший приоритет, чем запрет `DENY` на уровне таблицы.|  
  
 Параметр common criteria compliance enabled является дополнительным. Общие условия оцениваются и сертифицируются только для выпусков Enterprise и Datacenter. Последнее состояние сертификации общих условий см. на веб-сайте [Общие условия Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=616319) .  
  
> [!IMPORTANT]  
>  Помимо включения параметра common criteria compliance enabled, необходимо загрузить и выполнить скрипт, завершающий настройку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соответствия стандарту Common Criteria уровня 4 (EAL4+). Загрузить этот скрипт можно с сайта [Стандарт Common Criteria для Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=616319) .  
  
 Если для изменения значения параметра используется системная хранимая процедура `sp_configure`, изменить параметр common criteria compliance enabled можно только в случае, если параметр show advanced options равен 1. Установка параметра вступает в силу после перезапуска сервера. Возможные значения — 0 и 1.  
  
-   Значение 0 указывает, что соответствие стандарту Common Criteria не включено. Это значение по умолчанию.  
  
-   Значение 1 указывает, что соответствие стандарту Common Criteria включено.  
  
## <a name="examples"></a>Примеры  
 Следующий пример включает соответствие стандарту Common Criteria.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE WITH OVERRIDE; 
GO  
```  

Перезапустите [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  

