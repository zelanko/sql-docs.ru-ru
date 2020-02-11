---
title: Раздел журналов файлов настройки | Документация Майкрософт
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
ms.openlocfilehash: 14c5436478444e525c7a9753cf3e4e5cddb92f5d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922791"
---
# <a name="customization-file-logs-section"></a>Настройка раздела журналов файла
Раздел **журналы** содержит запись файла журнала, которая указывает имя файла, записывающего ошибки во время выполнения **операции.**  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись файла журнала имеет вид:  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Remarks  
  
|Часть|Description|  
|----------|-----------------|  
|**Err**|Литеральная строка, указывающая, что это запись файла журнала.|  
|*Файлов*|Полный путь и имя файла. Обычно используется имя файла **к:\мсдфмап.лог**.|  
  
 Файл журнала будет содержать имя пользователя, HRESULT, дату и время каждой ошибки.  
  
## <a name="see-also"></a>См. также:  
 [Раздел "Подключение файла настройки"](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел файла настройки SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList файла настройки](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


