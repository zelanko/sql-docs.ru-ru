---
title: Свойство ServerName (класс SqlServerAlias) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ServerName Property (SqlServerAlias Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 317035d73eae387b9de06324415b795693527489
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191571"
---
# <a name="servername-property-sqlserveralias-class"></a>Свойство ServerName (класс SqlServerAlias)
  Возвращает имя экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , заданного псевдонимом соединения сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.ServerName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServerAlias](sqlserveralias-class.md) , представляющий псевдоним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на который ссылается псевдоним соединения сервера.  
  
## <a name="remarks"></a>Примечания  
  