---
description: sp_helpmergedeleteconflictrows (Transact-SQL)
title: sp_helpmergedeleteconflictrows (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c4cda70ec894a50561cd62dc459bac915f437cc3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447048"
---
# <a name="sp_helpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о строках данных, утративших конфликты удаления. Эта хранимая процедура выполняется в базе данных публикации на издателе или в базе данных подписки на подписчике при использовании децентрализованной регистрации конфликтов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию **%** . Если указана публикация, возвращаются все конфликты, определенные этой публикацией.  
  
`[ @source_object = ] 'source_object'` Имя исходного объекта. *source_object* имеет тип **nvarchar (386)** и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'` Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar (386)**|Исходный объект для конфликта удаления.|  
|**уникаль**|**uniqueidentifier**|Идентификатор строки для конфликта удаления.|  
|**conflict_type**|**int**|Код, указывающий на тип конфликта.<br /><br /> **1** = Упдатеконфликт: конфликт обнаружен на уровне строк.<br /><br /> **2** = Колумнупдатеконфликт: конфликт обнаружен на уровне столбцов.<br /><br /> **3** = Упдатеделетевинсконфликт: Удаление побеждает в конфликте.<br /><br /> **4** = упдатевинсделетеконфликт: удаленный идентификатор rowguid, который потерял конфликт, записывается в эту таблицу.<br /><br /> **5** = Уплоадинсертфаилед: вставка из подписчика не может быть применена на издателе.<br /><br /> **6** = Довнлоадинсертфаилед: вставка из издателя не может быть применена на подписчике.<br /><br /> **7** = Уплоадделетефаилед: удаление на стороне подписчика не может быть отправлено на издатель.<br /><br /> **8** = Довнлоадделетефаилед: удаление на стороне издателя не может быть загружено на подписчик.<br /><br /> **9** = Уплоадупдатефаилед: обновление на стороне подписчика не может быть применено на издателе.<br /><br /> **10** = Довнлоадупдатефаилед: Update на стороне издателя не удалось применить к подписчику.|  
|**reason_code**|**Int**|Код ошибки, который может зависеть от контекста.|  
|**reason_text**|**varchar (720)**|Описание ошибки, которое может зависеть от контекста.|  
|**origin_datasource**|**varchar (255)**|Источник конфликта.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время, когда были добавлены сведения о конфликте.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helpmergedeleteconflictrows** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
