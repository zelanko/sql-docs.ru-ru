---
description: Диспетчер соединений «Очистка DQS»
title: Диспетчер подключений "Очистка DQS" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: faa1eedd-db14-41e5-8e58-8f0f6f561e42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33586839b3efb0c8c93786a2e020228a44dc6bbc
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726701"
---
# <a name="dqs-cleansing-connection-manager"></a>Диспетчер соединений «Очистка DQS»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Диспетчер соединений «Очистка DQS» позволяет пакету подключаться к серверу служб [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] . Преобразование «Очистка DQS» использует диспетчер соединений «Очистка DQS».  
  
 Дополнительные сведения о службах Data Quality Services см. в разделе [Data Quality Services Concepts](../../data-quality-services/data-quality-services-concepts.md).  
  
> [!IMPORTANT]  
>  Диспетчер соединений «Очистка DQS» поддерживает только проверку подлинности Windows.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами. Дополнительные сведения о свойствах, которые можно установить в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Диалоговое окно редактора преобразования "Очистка DQS"](../data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Дополнительные сведения о настройке диспетчера подключений программным образом см. в документации по классу <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> в руководстве для разработчиков.  
  
