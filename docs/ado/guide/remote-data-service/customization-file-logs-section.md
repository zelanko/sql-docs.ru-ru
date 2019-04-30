---
title: Файл настройки журналов разделе | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71a9130c385032acfad7c0c1040b293486bff525
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214905"
---
# <a name="customization-file-logs-section"></a>Настройка раздела журналов файла
**Журналы** раздел содержит запись файла журнала, который указывает имя файла, в который записываются ошибки во время работы **DataFactory**.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись файла журнала имеет вид:  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Примечания  
  
|Часть|Описание|  
|----------|-----------------|  
|**Err**|Строковый литерал, указывающий, является запись файла журнала.|  
|*FileName*|Полный путь и имя файла. Типичный файл называется **c:\msdfmap.log**.|  
  
 Файл журнала будет содержать имя пользователя, значение HRESULT, Дата и время каждой ошибки.  
  
## <a name="see-also"></a>См. также  
 [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


