---
title: Служба агент SQL Server не может использовать проверку подлинности SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036245"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Служба агента SQL Server не может использовать проверку подлинности SQL Server
  Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только проверку подлинности Windows, когда служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может осуществлять вход в базу данных только с проверкой подлинности Windows. Это означает, что учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна представлять пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Дополнительные сведения см. в разделах «Безопасность автоматического администрирования» и «Обеспечение безопасности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
