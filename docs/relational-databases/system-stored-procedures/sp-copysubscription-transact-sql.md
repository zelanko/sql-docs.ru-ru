---
title: sp_copysubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d3f67794eb2825c10b822ce719459b563f046d2
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304824"
---
# <a name="sp_copysubscription-transact-sql"></a>sp_copysubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Возможность присоединения подписок является устаревшей и в следующей версии будет удалена. Использовать эту функцию для новых разработок не рекомендуется. Для публикаций слиянием, секционированных с помощью параметризованных фильтров, рекомендуется использовать новые возможности секционированных снимков, которые упрощают инициализацию большого числа подписок. Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Для несекционированных публикаций можно инициализировать подписку с помощью резервной копии. Дополнительные сведения см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Копирует базу данных подписки, включающую подписки по запросу, но не принудительные подписки. Могут быть скопированы только те базы данных, которые состоят из одного файла. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @filename = ] 'file_name'` — это строка, указывающая полный путь, включая имя файла, в который сохраняется копия файла данных (MDF). *имя файла* имеет тип **nvarchar (260)** и не имеет значения по умолчанию.  
  
`[ @temp_dir = ] 'temp_dir'` — это имя каталога, содержащего временные файлы. *temp_dir* имеет тип **nvarchar (260)** и значение по умолчанию NULL. Если значение равно NULL, будет использоваться каталог данных по умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каталог должен включать достаточно свободного места для хранения файла с размером, равным суммарному размеру всех файлов баз данных подписчика.  
  
`[ @overwrite_existing_file = ] 'overwrite_existing_file'` является необязательным логическим флагом, указывающим, следует ли перезаписывать существующий файл с тем же именем, указанным в **\@filename**. *overwrite_existing_file*имеет **бит**и значение по умолчанию **0**. Если значение равно **1**, то файл, заданный параметром **\@filename**, перезаписывается, если он существует. Если значение **равно 0**, хранимая процедура завершается ошибкой, если файл существует, а файл не перезаписывается.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_copysubscription** используется во всех типах репликации для копирования базы данных подписки в файл в качестве альтернативы применению моментального снимка на подписчике. База данных должна быть настроена так, чтобы она поддерживала только подписки по запросу. Пользователи, имеющие необходимые разрешения, могут создать копии базы данных подписки, после чего отправить файл подписки (MSF-файл) по электронной почте, скопировать его или доставить другому подписчику, где этот файл можно будет подключить как подписку.  
  
 Размер копируемой базы данных подписки должен быть меньше 2 ГБ.  
  
 **sp_copysubscription** поддерживается только для баз данных с клиентскими подписками и не может выполняться, если база данных имеет серверные подписки.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_copysubscription**.  
  
## <a name="see-also"></a>См. также  
 [Альтернативные расположения папки моментальных снимков](../../relational-databases/replication/snapshot-options.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
