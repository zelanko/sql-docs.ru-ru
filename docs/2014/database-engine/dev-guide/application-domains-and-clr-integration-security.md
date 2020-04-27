---
title: Домены приложений и безопасность интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f2ff171562929a035cb80fed556c954508c5557
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62753776"
---
# <a name="application-domains-and-clr-integration-security"></a>Домены приложений и безопасность интеграции со средой CLR
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборки, принадлежащие одному и тому же владельцу, загружаются в одном и том же домене приложений. Благодаря тому, что весь набор сборок работает в одном и том же домене приложений, сборки могут обнаруживать друг друга во время выполнения с помощью API-интерфейсов отражения платформы .NET Framework или других средств, а также могут выполнять взаимные вызовы в режиме позднего связывания. Такие вызовы выполняются по отношению к сборкам, принадлежащим одному и тому же владельцу, поэтому для этих вызовов не проверяются разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Указанная схема размещения сборок в доменах приложений предназначена главным образом для обеспечения масштабируемости, безопасности и взаимной изоляции и может измениться в будущих версиях. Поэтому не следует рассчитывать на то, что всегда можно будет осуществлять поиск сборок в одном и том же домене приложений с помощью механизмов позднего связывания.  
  
## <a name="see-also"></a>См. также  
 [Безопасность интеграции со средой CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
