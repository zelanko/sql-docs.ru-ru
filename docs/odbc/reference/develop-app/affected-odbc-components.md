---
title: Затронутые компоненты ODBC Документы Майкрософт
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
ms.openlocfilehash: 8d9155fa1c9df5846f069e93a3db1b969e9219ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306478"
---
# <a name="affected-odbc-components"></a>Затрагиваемые компоненты ODBC
Обратная совместимость описывает, как приложения, менеджер драйверов и драйверы влияют на введение новой версии менеджера драйверов. Это влияет на приложения и драйвер, когда один или оба из них остаются в старой версии. Таким образом, существует три типа обратной совместимости, как показано в следующей таблице.  
  
|Тип|Версия DM|Версия приложения|Версия водителя|  
|----------|-------------------|----------------------------|-----------------------|  
|Обратная совместимость менеджера драйвера|*3.x*|*2.x*|*2.x*|  
|Обратная совместимость драйвера|*3.x*|*2.x*|*3.x*|  
|Обратная совместимость приложения|*3.x*|*3.x*|*2.x*|  
  
 Обратная совместимость драйверов в первую очередь обсуждается в приложении G: Driver Guidelines for Backward Compatibility.  
  
> [!NOTE]
>  Приложение, соответствующее стандартам, - например, приложение, написанное в соответствии со стандартами Open Group или ISO CLI, - гарантированно работает с драйвером ODBC *3.x* через диспетчера драйверов ODBC *3.x.* Предполагается, что функциональность, используемая приложением, доступна в драйвере. Предполагается также, что приложение, соответствующее стандартам, было составлено с помощью файлов заголовка ODBC *3.x.*
