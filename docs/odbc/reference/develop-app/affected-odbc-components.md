---
title: "Уязвимые компоненты ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2329ec013019ed11d63f9400014d718f55d7f217
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="affected-odbc-components"></a>Компоненты ODBC затронутых
Обратная совместимость описывается влияние приложений, диспетчер драйверов и драйверов с появлением новой версии диспетчера драйверов. Это влияет на приложения и драйвера при одной или обеих из них остаются в старой версии. Существует, поэтому три типа обратной совместимости, которые необходимо учитывать, как показано в следующей таблице.  
  
|Тип|Версия DM|Версия приложения|Версия драйвера|  
|----------|-------------------|----------------------------|-----------------------|  
|Обратная совместимость для диспетчера драйверов|3*.x*|2.*x*|2.*x*|  
|Обратная совместимость драйвера [1]|3*.x*|2.*x*|3.*x*|  
|Обратная совместимость приложений|3.*x*|3.*x*|2.*x*|  
  
 [1 обратной совместимости драйверов в основном рассматривается в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
> [!NOTE]  
>  Совместимый со стандартами приложения — например, приложение, которое будет записана в соответствии со стандартами Open Group или ISO CLI — гарантированно будет работать с ODBC 3*.x* драйвера, с помощью ODBC 3*.x*Диспетчера драйверов. Предполагается, что функциональные возможности, что приложение использует доступна в драйвере. Также предполагается, что стандартам приложение скомпилировано с ODBC 3*.x* файлы заголовков.
