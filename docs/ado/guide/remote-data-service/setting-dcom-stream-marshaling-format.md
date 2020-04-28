---
title: Настройка формата маршалирования потока DCOM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29bf8d19b9e3c9ec9b4072edd9575add9947c8f3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922216"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Настройка формата маршалинга потока DCOM
Клиентский компьютер, использующий компоненты RDS 1,5 или более ранней версии, несовместим с сервером, использующим компоненты RDS 2,0 или более поздней версии. При использовании DCOM в качестве базового протокола поддержка RDS 2,0 или более поздней версии более эффективна при переносе объектов [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) . Если клиент выполняет компоненты из RDS 1,5 или более ранней версии, можно настроить сервер для работы с предыдущей поддержкой RDS (называемой RDS 1,0) или более новой службой поддержки RDS (под названием RDS 2,0 или более поздней версии). Установите одну из следующих записей реестра:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -или-  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


