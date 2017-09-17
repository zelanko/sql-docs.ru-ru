---
title: "Включение библиотеки DLL для работы на DCOM | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e2d67a595c97547934b04794f036d58445e8c282
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Включение библиотеки DLL для запуска на DCOM
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ниже описывается включение DLL-библиотеку объектов бизнеса использование DCOM и Microsoft Internet сведения службы (HTTP) посредством служб компонентов.  
  
1.  Создайте новый пустой пакет в оснастке MMC служб компонентов.  
  
     Для создания пакета и добавить DLL-ФАЙЛ в этот пакет, будет использовать оснастки MMC служб компонентов. DLL-файл становится доступным через DCOM, однако она удаляет уровень доступа через службы IIS. (Если вы установите в реестре для DLL-файл, **Inproc** ключ теперь является пустым, присвоение атрибуту активации, описаны в дальнейшем в этом разделе добавляет значение в **Inproc** ключа.)  
  
2.  Для установки бизнес-объекта в пакете.  
  
     -или-  
  
     Импорт [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объект в пакет.  
  
3.  Задайте атрибут активации пакета **в процессе создателя** (Библиотечное приложение).  
  
     Чтобы DLL-файл доступен через DCOM и IIS на том же компьютере, необходимо задать атрибут активации компонента в оснастке MMC служб компонентов. После выбора атрибута **в процессе создателя**, можно будет заметить, что **Inproc** раздел реестра сервера был добавлен, точек для служб компонентов суррогатные DLL-файл.  
  
 Дополнительные сведения о служб компонентов (или Microsoft Transaction Service, если вы используете Windows NT) и как выполнить эти действия, веб-сервере транзакций Microsoft узле.



