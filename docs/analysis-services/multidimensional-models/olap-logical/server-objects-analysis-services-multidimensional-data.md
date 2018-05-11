---
title: Объекты сервера (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cfd88bb1f0d8b2b6ee4762afbcfcf76b56759a9c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="server-objects-analysis-services---multidimensional-data"></a>Объекты сервера (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-server-objects"></a>Знакомство с объектами серверов  
 <xref:Microsoft.AnalysisServices.Server> Объект представляет собой сервер и экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , необходимый для работы с.  
  
 Непосредственно после получения подключенного экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] появляется возможность просматривать следующее.  
  
-   Все базы данных, к которым может быть получен доступ, в виде коллекции.  
  
-   Все определенные свойства сервера в виде коллекции.  
  
-   Строка соединения, информация о соединении и идентификатор сеанса.  
  
-   Название продукта, выпуск и версия.  
  
-   Коллекции ролей.  
  
-   Коллекция трассировок.  
  
-   Коллекция сборок.  
  
  
