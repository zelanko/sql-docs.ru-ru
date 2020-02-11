---
title: Настройка виртуальных серверов в IIS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5888cb9666488ced6f9e112d21c48d0265f5c25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922838"
---
# <a name="configuring-virtual-servers-on-iis"></a>Настройка виртуальных серверов в IIS
При создании виртуальных серверов в службы IIS 4,0 необходимо выполнить следующие два дополнительных действия, чтобы настроить виртуальный сервер для работы с RDS:  
  
1.  При настройке сервера установите флажок "разрешить выполнение доступа".  
  
2.  Переместите мсадкс. dll в *VRoot*\мсадк, где *VRoot* — это корневой каталог виртуального сервера.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


