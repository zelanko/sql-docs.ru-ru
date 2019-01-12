---
title: Настройка раздела подключения файла | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 627bbbafd272b6bb7682b776132445041207f8e1
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133334"
---
# <a name="customization-file-connect-section"></a>Настройка раздела подключения файла
Обработчик по умолчанию — Запрет всех подключений. **Подключения** разделе укажет исключения этого поведения. Например, если все **подключения** разделы были отсутствует или пуст, то по умолчанию не может выполнять соединение.  
  
 **Подключения** раздел может содержать:  
  
-   Запись доступа по умолчанию, который указывает значение по умолчанию операции чтения и записи на этом компьютере. Если нет записи доступа по умолчанию в разделе, раздел будет игнорироваться.  
  
-   Новая строка подключения, заменяет строку подключения клиента.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа по умолчанию имеет вид:  
  
```console
  
Access=  
accessRight  
  
```  
  
 Запись строки соединения замены имеет вид:  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Примечания  
  
|Часть|Описание|  
|----------|-----------------|  
|**Подключить**|Строковый литерал, указывающий, является запись строки соединения.|  
|**_connectionString_**|Строка, которая заменяет всю клиентскую строку подключения.|  
|**Доступ**|Строковый литерал, указывающий, является запись доступа.|  
|**_accessRight_**|Один из следующих прав доступа:<br /><br /> -   **NoAccess** -пользователь не может получить доступ к источнику данных.<br />-   **Только для чтения** -пользователь может просматривать источника данных.<br />-   **ReadWrite** -пользователя можно считывать или записывать в источник данных.|  
  
 Если вы хотите разрешить любые соединения (в силу, отключение обработчика по умолчанию), установите элемент в **подключения по умолчанию** раздел `Access=ReadWrite`и удалите или закомментируйте любой другой **подключения** _идентификатор_ раздел.  
  
## <a name="see-also"></a>См. также  
 [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



