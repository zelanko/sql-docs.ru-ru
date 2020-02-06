---
title: Подготовка SQL Server для скрипта представления CDC-View Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d0c8f942-4c96-456f-ad10-577577c0f74e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 77f3575375ec991119462a5933e85df13de80795
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298691"
---
# <a name="prepare-sql-server-for-oracle-cdc-view-script"></a>Подготовка SQL Server для скрипта представления CDC Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Это диалоговое окно показывает скрипт подготовки SQL, с помощью которого создается база данных MSXDBCDC. Эта база данных должна быть на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы имелась возможность использовать ее вместе со службой Oracle CDC для SQL Server.  
  
 В диалоговом окне «Подготовка скрипта SQL Server» выполните следующие действия.  
  
 **Сохранить как**  
 Сохранение скрипта в текстовый файл, который можно разместить в любом каталоге. Эти скрипты можно будет запустить позднее путем их вставки в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Copy**.  
 Копирует скрипт в буфер обмена. Затем можно скопировать скрипт в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для его выполнения и создания базы данных MSXDBCDC.  
  
## <a name="see-also"></a>См. также:  
 [Подготовка SQL Server для CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
