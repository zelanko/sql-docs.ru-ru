---
title: Настройка файла раздела UserList | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5feb29337ccd0ee79cd1b6f98187cc6fdb52a942
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214785"
---
# <a name="customization-file-userlist-section"></a>Настройка раздела UserList файла
**Userlist** раздел относится к **подключения** раздел с тот же раздел *идентификатор* параметра.  
  
 Этот раздел может содержать *доступом пользователя*, который указывает доступа права для указанного пользователя и переопределяет *по умолчанию* *доступ к записи* в соответствующем **подключения** раздел.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа пользователя имеет вид:  
  
 _имя пользователя_ **=**   
 **_accessRights_**  
  
|Часть|Описание|  
|----------|-----------------|  
|*userName*|*Имя пользователя* лица, применение этого подключения. Допустимые имена пользователей, устанавливаются со службами IIS **Service Manager** диалоговое окно.|  
|**_accessRights_**|Один из следующих прав доступа:<br /><br /> -   **NoAccess** -пользователь не может получить доступ к источнику данных.<br />-   **Только для чтения** -пользователь может просматривать источника данных.<br />-   **ReadWrite** -пользователя можно считывать или записывать в источник данных.|  
  
## <a name="see-also"></a>См. также  
 [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


