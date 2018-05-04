---
title: dbo.sysschedules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysschedules_TSQL
- sysschedules
- sysschedules_TSQL
- dbo.sysschedules
dev_langs:
- TSQL
helpviewer_keywords:
- sysschedules system table
ms.assetid: 4cac9237-7a69-4035-bb3e-928b76aad698
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e051217a00c98b0571f9d68ebfa4f844916d7984
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dbosysschedules-transact-sql"></a>dbo.sysschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о расписании заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**schedule_uid**|**uniqueidentifier**|Уникальный идентификатор расписания заданий. Это значение используется, чтобы определить расписание для распределенных заданий.|  
|**originating_server_id**|**int**|Идентификатор главного сервера, с которого поступило расписание заданий.|  
|**name**|**sysname (nvarchar(128))**|Пользовательское имя для расписания заданий. Это имя должно быть уникальным в пределах задания.|  
|**owner_sid**|**varbinary(85)**|Microsoft Windows *security_identifier* пользователя или группы, которой принадлежит расписания задания.|  
|**Включен**|**int**|Состояние расписания заданий:<br /><br /> **0** — не включено.<br /><br /> **1** = включен.<br /><br /> Если расписание не включено, никакие задания не будут выполняться по этому расписанию.|  
|**freq_type**|**int**|С какой частотой выполняется задание по этому расписанию:<br /><br /> **1** = только один раз<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно, относительно **freq_interval**<br /><br /> **64** = выполняется при запуске службы агента SQL Server<br /><br /> **128** = выполняется, когда компьютер простаивает|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Зависит от значения **freq_type**. Значение по умолчанию — **0**, что означает, что **freq_interval** не используется. В приведенной ниже таблице для возможных значений и их последствия.|  
|**freq_subday_type**|**int**|Единицы измерения для **freq_subday_interval**. Ниже приведены возможные значения и их описания.<br /><br /> <br /><br /> **1** : в указанное время<br /><br /> **2** : секунд<br /><br /> **4** : минут<br /><br /> **8** : часы|  
|**freq_subday_interval**|**int**|Число **freq_subday_type** периодов должно пройти между выполнениями задания.|  
|**freq_relative_interval**|**int**|Когда **freq_interval** происходит в каждом месяце, если **freq_interval** — **32** (относительно ежемесячно). Может использоваться одно из следующих значений:<br /><br /> **0** = **freq_relative_interval** не используется<br /><br /> **1** = первый<br /><br /> **2** = секунды<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = последний|  
|**freq_recurrence_**<br /><br /> **Коэффициент**|**int**|Число недель или месяцев между запланированными выполнениями задания. **freq_recurrence_factor** используется только в том случае, если **freq_type** — **8**, **16**, или **32**. Если этот столбец содержит **0**, **freq_recurrence_factor** не используется.|  
|**active_start_date**|**int**|Дата, когда может начаться выполнение задания. Формат даты: ГГГГMMДД. Значение NULL указывает на сегодняшнюю дату.|  
|**active_end_date**|**int**|Дата, когда может быть остановлено выполнение задания. Формат даты установлен как: ГГГГMMДД.|  
|**active_start_time**|**int**|Время в любой день между **active_start_date** и **active_end_date** начинается выполнение этого задания. Формат времени ЧЧMMСС, с использованием 24-часового измерения суток.|  
|**active_end_time**|**int**|Время в любой день между **active_start_date** и **active_end_date** останавливается выполнение этого задания. Формат времени ЧЧMMСС, с использованием 24-часового измерения суток.|  
|**date_created**|**datetime**|Дата и время, когда было создано расписание.|  
|**date_modified**|**datetime**|Дата и время, когда расписание было последний раз изменено.|  
|**version_number**|**int**|Номер текущей версии расписания. Например, если расписание подвергалось изменению 10 раз **version_number** — 10.|  
  
|Значение аргумента freq_type|Результат воздействия на аргумент freq_interval|  
|-------------------------|------------------------------|  
|**1** (один раз)|**freq_interval** не используется (**0**)|  
|**4** (ежедневно)|Каждый **freq_interval** дней|  
|**8** (еженедельно)|**freq_interval** — один или несколько из следующих действий:<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **4** = Вторник<br /><br /> **8** = среда<br /><br /> **16** = четверг<br /><br /> **32** = Пятница<br /><br /> **64** = суббота|  
|**16** (ежемесячно)|На **freq_interval** день месяца|  
|**32** (ежемесячно, относительный)|**freq_interval** является одним из следующих:<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **3** = Вторник<br /><br /> **4** = среда<br /><br /> **5** = четверг<br /><br /> **6** = Пятница<br /><br /> **7** = суббота<br /><br /> **8** = день<br /><br /> **9** = рабочий день<br /><br /> **10** = выходной день|  
|**64** (запускается при запуске службы агента SQL Server)|**freq_interval** не используется (**0**)|  
|**128** (запускается при простое компьютера)|**freq_interval** не используется (**0**)|  
  
## <a name="see-also"></a>См. также:  
 [dbo.sysjobschedules & #40; Transact-SQL & #41;](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
  
  
