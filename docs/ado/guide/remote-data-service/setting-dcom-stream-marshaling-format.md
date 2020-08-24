---
description: Настройка формата маршалинга потока DCOM
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 42d49824bc814026348c6f3aef99860b40f20f76
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759264"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Настройка формата маршалинга потока DCOM
Клиентский компьютер, использующий компоненты RDS 1,5 или более ранней версии, несовместим с сервером, использующим компоненты RDS 2,0 или более поздней версии. При использовании DCOM в качестве базового протокола поддержка RDS 2,0 или более поздней версии более эффективна при переносе объектов [набора записей](../../reference/ado-api/recordset-object-ado.md) . Если клиент выполняет компоненты из RDS 1,5 или более ранней версии, можно настроить сервер для работы с предыдущей поддержкой RDS (называемой RDS 1,0) или более новой службой поддержки RDS (под названием RDS 2,0 или более поздней версии). Установите одну из следующих записей реестра:  
  
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