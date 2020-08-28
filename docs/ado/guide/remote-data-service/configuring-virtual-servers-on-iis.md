---
description: Настройка виртуальных серверов в IIS
title: Настройка виртуальных серверов в IIS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: rothja
ms.author: jroth
ms.openlocfilehash: 53d22155f8e7af894419a28ddf01bf3fe80e34f3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978285"
---
# <a name="configuring-virtual-servers-on-iis"></a>Настройка виртуальных серверов в IIS
При создании виртуальных серверов в службы IIS 4,0 необходимо выполнить следующие два дополнительных действия, чтобы настроить виртуальный сервер для работы с RDS:  
  
1.  При настройке сервера установите флажок "разрешить выполнение доступа".  
  
2.  Переместите msadcs.dll в *VRoot*\мсадк, где *VRoot* — это корневой каталог виртуального сервера.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](./rds-fundamentals.md)