---
title: Уязвимые компоненты ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a35f04a2e4cf540c5e2419f9bb1616b3ff02d8f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="affected-odbc-components"></a>Компоненты ODBC затронутых
Обратная совместимость описывается влияние приложений, диспетчер драйверов и драйверов с появлением новой версии диспетчера драйверов. Это влияет на приложения и драйвера при одной или обеих из них остаются в старой версии. Существует, поэтому три типа обратной совместимости, которые необходимо учитывать, как показано в следующей таблице.  
  
|Тип|Версия DM|Версия приложения|Версия драйвера|  
|----------|-------------------|----------------------------|-----------------------|  
|Обратная совместимость для диспетчера драйверов|3 *.x*|2.*x*|2.*x*|  
|Обратная совместимость драйвера [1]|3 *.x*|2.*x*|3.*x*|  
|Обратная совместимость приложений|3.*x*|3.*x*|2.*x*|  
  
 [1 обратной совместимости драйверов в основном рассматривается в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
> [!NOTE]  
>  Совместимый со стандартами приложения — например, приложение, которое будет записана в соответствии со стандартами Open Group или ISO CLI — гарантированно будет работать с ODBC 3 *.x* драйвера, с помощью ODBC 3 *.x*Диспетчера драйверов. Предполагается, что функциональные возможности, что приложение использует доступна в драйвере. Также предполагается, что стандартам приложение скомпилировано с ODBC 3 *.x* файлы заголовков.
