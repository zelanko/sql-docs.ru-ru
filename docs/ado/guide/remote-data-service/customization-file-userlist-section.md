---
title: Настройки файла UserList раздел | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0184e0289a5f56904e87360900be2409b6d2f248
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="customization-file-userlist-section"></a>Раздел UserList настройки файла
**Userlist** раздел относится к **подключения** раздел с тот же раздел *идентификатор* параметра.  
  
 Этот раздел может содержать *запись доступа пользователя*, который определяет доступа для указанного пользователя и переопределений *по умолчанию* *доступ к записи* в соответствующем **подключения** раздела.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Доступ пользователя в записи имеет следующую форму:  
  
 *Имя пользователя* **=**   
 ***accessRights***  
  
|Часть|Описание|  
|----------|-----------------|  
|*userName*|*Имя пользователя* пользователя, при использовании этого подключения. Допустимые имена пользователей, установленных с IIS **Service Manager** диалогового окна.|  
|***accessRights***|Одно из следующих прав:<br /><br /> -   **NoAccess** — пользователь не может получить доступ к источнику данных.<br />-   **Только для чтения** — пользователь может просматривать источника данных.<br />-   **ReadWrite** — пользователь может считывать или запись в источнике данных.|  
  
## <a name="see-also"></a>См. также  
 [Файл настроек присоединения раздела](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел журналы настройки файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел SQL настройки файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Основные сведения о настройке файла](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


