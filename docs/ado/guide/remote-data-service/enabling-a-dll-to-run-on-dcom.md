---
description: Разрешение запуска библиотеки DLL в DCOM
title: Включение запуска DLL на DCOM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: rothja
ms.author: jroth
ms.openlocfilehash: d685e03834b1c8390ddd51a8e590f25cd6307efe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452206"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Разрешение запуска библиотеки DLL в DCOM
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ниже показано, как включить для бизнес-объекта. dll использование DCOM и Microsoft службы IIS (HTTP) через службы компонентов.  
  
1.  Создайте новый пустой пакет в оснастке MMC "службы компонентов".  
  
     Используйте оснастку MMC "службы компонентов" для создания пакета и добавления библиотеки DLL в этот пакет. Это делает библиотеку DLL доступной через DCOM, но она удаляет специальные возможности через IIS. (При возврате реестра для DLL-файла **процедура INPROC** теперь пуста; Установка атрибута активации, описанного далее в этом разделе, добавляет значение в ключ **INPROC** .)  
  
2.  Установите бизнес-объект в пакет.  
  
     -или-  
  
     Импортируйте объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject в пакет.  
  
3.  Установите атрибут активации для пакета **в в процессе создателя** (приложение библиотеки).  
  
     Чтобы сделать библиотеку DLL доступной через DCOM и службы IIS на том же компьютере, необходимо задать атрибут активации компонента в оснастке MMC "службы компонентов". После присвоения атрибуту значения **в процессе создателя**вы заметите, что был добавлен ключ сервера **INPROC** в реестр, указывающий на суррогатную библиотеку служб компонентов.  
  
 Дополнительные сведения о службах компонентов (или Microsoft Transaction Service, если используется Windows NT) и о том, как выполнить эти действия, см. на веб-сайте Microsoft Transaction Server.


