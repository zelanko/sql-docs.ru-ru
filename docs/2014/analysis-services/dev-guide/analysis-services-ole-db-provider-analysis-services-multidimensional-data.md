---
title: Службы Analysis Services поставщика OLE DB (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services OLE DB Provider
ms.assetid: cdeecd50-1d91-4162-a4a2-01c7799b02a8
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32c717ef25e95192bceaa7084f3c8de63600f834
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189152"
---
# <a name="analysis-services-ole-db-provider-analysis-services---multidimensional-data"></a>Поставщик OLE DB служб Analysis Services (службы Analysis Services — многомерные данные)
  Поставщик Analysis Services OLE DB является интерфейсом для приложений, взаимодействующих с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Используется для построения клиентских приложений, взаимодействующих с многомерными данными. Этот поставщик также предоставляет методы для интеллектуального анализа многомерных данных и реляционных данных как в сети, так и вне сети. Поставляется в составе служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Его можно распространять в сторонних клиентских приложениях.  
  
 Поставщик OLE DB служб Analysis Services — это основной метод взаимодействия со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для выполнения таких задач, как соединение с кубом или моделью интеллектуального анализа данных, направление запросов к кубу или модели интеллектуального анализа данных и получение сведений о схеме.  
  
 В качестве изолированного поставщика поставщик OLE DB служб Analysis Services предоставляет клиентским приложениям возможность создавать файлы локальных кубов и модели интеллектуального анализа данных из реляционных и многомерных источников. Клиентские приложения могут соединяться с локальным кубом и выполнять запросы с многомерными выражениями, без взаимодействия с полномасштабным сервером, который работает с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Доступ к данным многомерной модели &#40;службы Analysis Services — многомерные данные&#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  