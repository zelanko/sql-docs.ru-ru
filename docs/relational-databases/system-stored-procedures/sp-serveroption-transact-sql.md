---
title: sp_serveroption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1fcd6f158908893ce5eb86c24a3bb3882867bc2d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104385"
---
# <a name="sp_serveroption-transact-sql"></a>sp_serveroption (Transact-SQL)
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
`[ @server = ] 'server'`Имя сервера, для которого необходимо задать параметр. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @optname = ] 'option_name'`Параметр, заданный для указанного сервера. *option_name* имеет тип **varchar (** 35 **)** и не имеет значения по умолчанию. *option_name* может иметь любое из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**совместимые параметры сортировки**|Влияет на выполнение распределенных запросов на связанных серверах. Если этот параметр имеет значение **true**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предполагается, что все символы на связанном сервере совместимы с локальным сервером, в зависимости от набора символов и порядка сортировки (или порядка сортировки). Это позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправлять поставщику сравнения по символьным столбцам. Если этот параметр не задан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда выполняет сравнения по символьным столбцам локально.<br /><br /> Этот параметр необходимо задать только в том случае, если источник данных, соответствующий связанному серверу, имеет тот же набор символов и тот же порядок сортировки, что и локальный сервер.|  
|**имя параметров сортировки**|Задает имя параметров сортировки, используемых удаленным источником данных, если параметр **use remote collation** имеет **значение true** , а источник данных не является источником [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных. Этот имя должно быть одним из параметров сортировки, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Этот параметр используется при доступе к источнику данных OLE DB, отличному от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], параметры сортировки которого совпадают с одним из параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Связанный сервер должен поддерживать использование единых параметров сортировки для всех столбцов на этом сервере. Не задавайте этот параметр, если связанный сервер поддерживает несколько параметров сортировки для одного источника данных, или если невозможно определить, соответствуют ли параметры сортировки связанного сервера одному из параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**время ожидания подключения**|Время ожидания для подключения к связанному серверу (в секундах).<br /><br /> Если значение **равно 0**, используйте **sp_configure** по умолчанию.|  
|**доступ к данным**|Разрешает и запрещает доступ распределенных запросов к связанному серверу. Может использоваться только для записей **sys. Server** , добавленных с помощью **sp_addlinkedserver**.|  
|**dist**|Распространитель.|  
|**lazy schema validation**|Определяет, будет ли проверена схема удаленных таблиц.<br /><br /> Если **значение — true**, пропускать проверку схемы удаленных таблиц в начале запроса.|  
|**pub**|Издатель.|  
|**время ожидания запроса**|Значение времени ожидания для запросов к связанному серверу.<br /><br /> Если значение **равно 0**, используйте **sp_configure** по умолчанию.|  
|**удаленного**|Включает вызов RPC с заданного сервера.|  
|**RPC out**|Включает вызов RPC на заданный сервер.|  
|**Директор**|Подписчик.|  
|**система**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**использовать удаленные параметры сортировки**|Определяет, будут ли использоваться параметры сортировки удаленного столбца или локального сервера.<br /><br /> Если **значение — true**, параметры сортировки удаленных столбцов используются для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источников данных, а параметры сортировки, заданные в **имени параметров сортировки** , используются для источников,[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не являющихся источниками данных.<br /><br /> Если **значение равно "false**", распределенные запросы всегда будут использовать параметры сортировки по умолчанию локального сервера, в то время как **имя параметров сортировки** и параметры сортировки удаленных столбцов игнорируются. Значение по умолчанию — **false**. (Значение **false** совместимо с семантикой параметров сортировки, используемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0.)|  
|**remote proc transaction promotion**|Используйте этот параметр, чтобы защитить действия процедуры между серверами посредством транзакции координатора распределенных транзакций (Майкрософт) ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] DTC). Если этот параметр имеет значение TRUE (или ON), то вызов удаленной хранимой процедуры приводит к запуску распределенной транзакции и прикрепляется к выполнению транзакции MS DTC. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вызывающий удаленную хранимую процедуру, является инициатором транзакции и контролирует ее завершение. Когда последующая инструкция COMMIT TRANSACTION или ROLLBACK TRANSACTION выдается для соединения, контролирующий экземпляр предписывает MS DTC управлять завершением распределенной транзакции на всех вовлеченных компьютерах.<br /><br /> После запуска распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)] вызовы удаленных хранимых процедур могут выполняться к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенным в качестве связанных серверов. Все связанные серверы перечислены в распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)], а координатор распределенных транзакций (Майкрософт) обеспечивает завершение транзакции на каждом из связанных серверов.<br /><br /> Если этот параметр имеет значение FALSE (или OFF), локальная транзакция не станет распределенной при удаленном вызове процедуры на связанном сервере.<br /><br /> Если до выполнения вызова процедуры сервер-сервер транзакция уже является распределенной, этот параметр не действует. Вызов процедуры на связанном сервере будет выполняться в одной распределенной транзакции.<br /><br /> Если до вызова процедуры сервер-сервер у соединения нет активной транзакции, этот параметр не действует. Процедура выполняется на связанном сервере без активных транзакций.<br /><br /> Значение по умолчанию для данного параметра равно TRUE (или ON).|  
  
`[ @optvalue = ] 'option_value'`Указывает, следует ли включать *option_name* (**true** или **On**) или Disabled (**false** или **Off**). *option_value* имеет тип **varchar (** 10 **)** и не имеет значения по умолчанию.  
  
 *option_value* может быть неотрицательным целым числом для параметров **времени ожидания соединения** и **времени ожидания запроса** . Для параметра **имя параметров сортировки** *option_value* может быть именем параметров сортировки или null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Если параметру **совместимости с параметрами сортировки** присвоено значение true, то **имя параметров сортировки** автоматически будет иметь значение null. Если для **имени параметров сортировки** задано значение, не равное NULL, то **Параметры сортировки, совместимые** с, автоматически устанавливаются в значение false.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LINKED SERVER на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере связанный сервер настраивается в соответствии с другим экземпляром сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, чтобы тот был совместим по параметрам сортировки с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры распределенных запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
