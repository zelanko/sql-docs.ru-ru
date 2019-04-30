---
title: Затронутые компоненты ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e004e6fd41ee74643fc05ec9020e6ac1933e09
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186257"
---
# <a name="affected-odbc-components"></a>Затрагиваемые компоненты ODBC
Обратная совместимость Описывает влияние приложений, диспетчер драйверов и драйверов с появлением новой версии диспетчера драйверов. Это влияет на приложения и драйвера при одно или оба из них остаются в старой версии. Существует, поэтому три типа обратной совместимости, которые необходимо учитывать, как показано в следующей таблице.  
  
|Тип|Версия DM|Версия приложения|Версия драйвера|  
|----------|-------------------|----------------------------|-----------------------|  
|Обратная совместимость из диспетчера драйверов|3 *.x*|2.*x*|2.*x*|  
|Обратная совместимость драйвера [1]|3 *.x*|2.*x*|3.*x*|  
|Обратная совместимость приложений|3.*x*|3.*x*|2.*x*|  
  
 [1] обратная совместимость драйверы в первую очередь рассматривается в приложении G: Рекомендации по драйверов для обеспечения обратной совместимости.  
  
> [!NOTE]
>  Соответствующих стандартам приложений — например, приложение, которое будет записана в соответствии со стандартами Open Group или интерфейса командной строки ISO - гарантируется для работы с ODBC 3 *.x* драйвер ODBC 3 *.x*Диспетчера драйверов. Предполагается, что приложение использует функциональность доступна в драйвере. Также предполагается, что соответствующие стандартам приложения был скомпилирован с ODBC 3 *.x* файлы заголовков.
