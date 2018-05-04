---
title: Объекты сервера (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6b92d8f3f94547e291aa64a9870fdf8bb3926e3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
