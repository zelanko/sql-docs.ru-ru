---
title: Диспетчер подключений "Очистка DQS" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: faa1eedd-db14-41e5-8e58-8f0f6f561e42
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ceddb40eee5f5eafcc134e4ed434c2dabadd6896
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728282"
---
# <a name="dqs-cleansing-connection-manager"></a>Диспетчер соединений «Очистка DQS»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диспетчер соединений «Очистка DQS» позволяет пакету подключаться к серверу служб [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] . Преобразование «Очистка DQS» использует диспетчер соединений «Очистка DQS».  
  
 Дополнительные сведения о службах Data Quality Services см. в разделе [Data Quality Services Concepts](../../data-quality-services/data-quality-services-concepts.md).  
  
> [!IMPORTANT]  
>  Диспетчер соединений «Очистка DQS» поддерживает только проверку подлинности Windows.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами. Дополнительные сведения о свойствах, которые можно установить в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Диалоговое окно редактора преобразования "Очистка DQS"](../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
 Дополнительные сведения о настройке диспетчера подключений программным образом см. в документации по классу <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> в руководстве для разработчиков.  
  
  
