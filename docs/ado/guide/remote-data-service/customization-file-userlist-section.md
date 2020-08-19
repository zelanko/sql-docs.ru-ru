---
description: Настройка раздела UserList файла
title: Раздел UserList файла настройки | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: afdd3560de5ca7e64d8a378f1eca04f875903a06
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452236"
---
# <a name="customization-file-userlist-section"></a>Настройка раздела UserList файла
Раздел **USERLIST** относится к разделу **Connect** с тем же параметром *идентификатора* раздела.  
  
 Этот раздел может содержать *запись доступа пользователя*, которая задает права доступа для указанного пользователя и переопределяет *запись доступа* *по умолчанию* в соответствующем разделе **Connect** .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа пользователя имеет вид:  
  
 _имя пользователя_**=**   
 **_accessRights_**  
  
|Часть|Описание|  
|----------|-----------------|  
|*userName*|*Имя пользователя* , использующего это подключение. Допустимые имена пользователей устанавливаются в диалоговом окне IIS **Service Manager** .|  
|**_accessRights_**|Одно из следующих прав доступа:<br /><br /> -   Не **доступ** — пользователь не может получить доступ к источнику данных.<br />-   **Только для** чтения — пользователь может читать источник данных.<br />-   **ReadWrite** — пользователь может выполнять чтение или запись в источник данных.|  
  
## <a name="see-also"></a>См. также  
 [Раздел "Подключение файла настройки"](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел журналов файлов настройки](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел файла настройки SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


