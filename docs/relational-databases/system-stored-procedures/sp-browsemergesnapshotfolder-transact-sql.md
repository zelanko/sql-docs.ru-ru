---
title: sp_browsemergesnapshotfolder (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e03232e394adcb6c6ee8fcf208754cf72ca9e951
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85873888"
---
# <a name="sp_browsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает полный путь для последнего моментального снимка, сформированного для публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar (2000)**|Полный путь к каталогу моментальных снимков.|  
  
## <a name="remarks"></a>Комментарии  
 **sp_browsemergesnapshotfolder** используется в репликации слиянием.  
  
 Если публикация настроена на формирование файлов моментального снимка в рабочем каталоге издателя и папке моментальных снимков издателя, то результирующий набор будет состоять из двух строк: первая строка будет содержать папку моментальных снимков публикации, а вторая — рабочий каталог издателя.  
  
 **sp_browsemergesnapshotfolder** удобно использовать для определения каталога, в котором создаются файлы моментальных снимков слияния. Данная папка или путь и ее содержимое затем могут быть скопированы на съемный носитель, а моментальный снимок используется для синхронизации подписки из альтернативного места хранения моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_browsemergesnapshotfolder**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
