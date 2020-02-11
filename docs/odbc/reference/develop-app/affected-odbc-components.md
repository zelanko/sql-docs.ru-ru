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
ms.openlocfilehash: 08997f610b00f22d436a5c91d34beb2a8fc2cc1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67944857"
---
# <a name="affected-odbc-components"></a>Затрагиваемые компоненты ODBC
Обратная совместимость. описание того, как повлияли приложения, диспетчер драйверов и драйверы на введение новой версии диспетчера драйверов. Это влияет на приложения и драйверы, если один или оба они остаются в старой версии. Поэтому следует учитывать три типа обратной совместимости, как показано в следующей таблице.  
  
|Тип|Версия DM|Версия приложения|Версия драйвера|  
|----------|-------------------|----------------------------|-----------------------|  
|Обратная совместимость диспетчера драйверов|*3.x*|*2.x*|*2.x*|  
|Обратная совместимость драйвера [1]|*3.x*|*2.x*|*3.x*|  
|Обратная совместимость приложения|*3.x*|*3.x*|*2.x*|  
  
 [1] обратная совместимость драйверов в основном обсуждается в приложении G: рекомендации по драйверам для обеспечения обратной совместимости.  
  
> [!NOTE]
>  Приложение, совместимое с стандартам. Например, приложение, написанное в соответствии с общедоступной группой или стандартом ISO CLI, гарантированно работает с драйвером ODBC *3* . x с помощью ДИСПЕТЧЕРА драйверов ODBC *3. x* . Предполагается, что функция, используемая приложением, доступна в драйвере. Также предполагается, что приложение, соответствующее стандартам, было скомпилировано с файлами заголовков ODBC *3. x* .
