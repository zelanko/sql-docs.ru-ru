---
description: Затрагиваемые компоненты ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4874a22d441ec856c25e08dc20cf04e0f0be89cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424866"
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
