---
title: Служба агента SQL Server нельзя использовать проверку подлинности SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ddda041de230fb13e2f743edc2c3867f9716c180
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194643"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Служба агента SQL Server не может использовать проверку подлинности SQL Server
  Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только проверку подлинности Windows, когда служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может осуществлять вход в базу данных только с проверкой подлинности Windows. Это означает, что учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна представлять пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Дополнительные сведения см. в разделах «Безопасность автоматического администрирования» и «Обеспечение безопасности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  