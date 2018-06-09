---
title: sp_serveroption (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_serveroption_TSQL
- sp_serveroption
dev_langs:
- TSQL
helpviewer_keywords:
- 7343 (Database Engine error)
- sp_serveroption
ms.assetid: 47d04a2b-dbf0-4f15-bd9b-81a2efc48131
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 99f936f0a8d127dd33ebce8b86c0a958cafccf66
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "33260950"
---
# <a name="spserveroption-transact-sql"></a>sp_serveroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает параметры сервера для удаленных и связанных серверов.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_serveroption [@server = ] 'server'   
      ,[@optname = ] 'option_name'       
      ,[@optvalue = ] 'option_value' ;  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@server =** ] **'***server***'**  
 Имя сервера, для которого задается параметр. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [  **@optname =** ] **"***option_name***"**  
 Параметр, задаваемый для указанного сервера. *option_name* — **varchar (** 35 **)**, не имеет значения по умолчанию. *option_name* может иметь любое из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**совместимые параметры сортировки**|Влияет на выполнение распределенных запросов на связанных серверах. Если этот параметр имеет значение **true**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предполагается, что все символы на связанном сервере совместимы с локальным сервером в отношении символов и параметров сортировки (или порядка сортировки). Это позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправлять поставщику сравнения по символьным столбцам. Если этот параметр не задан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда выполняет сравнения по символьным столбцам локально.<br /><br /> Этот параметр необходимо задать только в том случае, если источник данных, соответствующий связанному серверу, имеет тот же набор символов и тот же порядок сортировки, что и локальный сервер.|  
|**Имя параметров сортировки**|Указывает имя параметров сортировки, используемое удаленным источником данных, если **использовать удаленные параметры сортировки** — **true** и источник данных не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных. Этот имя должно быть одним из параметров сортировки, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Этот параметр используется при доступе к источнику данных OLE DB, отличному от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], параметры сортировки которого совпадают с одним из параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Связанный сервер должен поддерживать использование единых параметров сортировки для всех столбцов на этом сервере. Не задавайте этот параметр, если связанный сервер поддерживает несколько параметров сортировки для одного источника данных, или если невозможно определить, соответствуют ли параметры сортировки связанного сервера одному из параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Время ожидания подключения**|Время ожидания valuein секунд для подключения к связанному серверу.<br /><br /> Если **0**, используйте **sp_configure** по умолчанию.|  
|**Доступ к данным**|Разрешает и запрещает доступ распределенных запросов к связанному серверу. Может использоваться только для **sys.server** записи, добавленные с помощью **sp_addlinkedserver**.|  
|**dist**|Распространитель.|  
|**Отложенная проверка схемы**|Определяет, будет ли проверена схема удаленных таблиц.<br /><br /> Если **true**, пропустить проверка схемы удаленных таблиц в начале запроса.|  
|**pub**|Издатель.|  
|**время ожидания запроса**|Значение времени ожидания для запросов к связанному серверу.<br /><br /> Если **0**, используйте **sp_configure** по умолчанию.|  
|**rpc**|Включает вызов RPC с заданного сервера.|  
|**RPC out**|Включает вызов RPC на заданный сервер.|  
|**sub**|Подписчик.|  
|**Системы**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**использовать удаленные параметры сортировки**|Определяет, будут ли использоваться параметры сортировки удаленного столбца или локального сервера.<br /><br /> Если **true**, параметры сортировки удаленных столбцов используются для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источники данных и параметры сортировки, указанные в **имя параметров сортировки** используется для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источники данных.<br /><br /> Если **false**, распределенных запросах всегда будут использоваться параметры сортировки по умолчанию на локальном сервере, пока **имя параметров сортировки** и параметры сортировки удаленных столбцов игнорируются. Значение по умолчанию — **false**. ( **False** значение совместимо с семантикой параметров сортировки, используемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.)|  
|**Повышение транзакции удаленного процесса**|Используйте этот параметр, чтобы защитить действия процедуры между серверами посредством транзакции координатора распределенных транзакций (Майкрософт) ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] DTC). Если этот параметр имеет значение TRUE (или ON) вызов удаленной хранимой процедуры запускает распределенную транзакцию и прикрепляет к транзакции с MS DTC. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вызывающий удаленную хранимую процедуру, является инициатором транзакции и контролирует ее завершение. Когда последующая инструкция COMMIT TRANSACTION или ROLLBACK TRANSACTION выдается для соединения, контролирующий экземпляр предписывает MS DTC управлять завершением распределенной транзакции на всех вовлеченных компьютерах.<br /><br /> После запуска распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)] вызовы удаленных хранимых процедур могут выполняться к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенным в качестве связанных серверов. Все связанные серверы перечислены в распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)], а координатор распределенных транзакций (Майкрософт) обеспечивает завершение транзакции на каждом из связанных серверов.<br /><br /> Если этот параметр имеет значение FALSE (или OFF), локальная транзакция не станет распределенной при удаленном вызове процедуры на связанном сервере.<br /><br /> Если до выполнения вызова процедуры сервер-сервер транзакция уже является распределенной, этот параметр не действует. Вызов процедуры на связанном сервере будет выполняться в одной распределенной транзакции.<br /><br /> Если до вызова процедуры сервер-сервер у соединения нет активной транзакции, этот параметр не действует. Процедура выполняется на связанном сервере без активных транзакций.<br /><br /> Значение по умолчанию для данного параметра равно TRUE (или ON).|  
  
 [  **@optvalue =**] **"***option_value***"**  
 Указывает ли *option_name* должен быть включен (**TRUE** или **на**) или отключена (**FALSE** или **off**). *option_value* — **varchar (** 10 **)**, не имеет значения по умолчанию.  
  
 *option_value* может быть неотрицательным целым числом для **время ожидания подключения** и **время ожидания запроса** параметры. Для **имя параметров сортировки** параметр *option_value* может представлять собой имя параметров сортировки или NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если **совместимости параметров сортировки** параметр имеет значение TRUE, **имя параметров сортировки** автоматически будет иметь значение NULL. Если **имя параметров сортировки** задано ненулевое значение, **совместимости параметров сортировки** автоматически будет установлен в значение FALSE.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LINKED SERVER на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере связанный сервер настраивается в соответствии с другим экземпляром сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, чтобы тот был совместим по параметрам сортировки с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
## <a name="see-also"></a>См. также  
 [Распределенные запросы хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
