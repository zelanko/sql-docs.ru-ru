---
title: Библиотека курсоров ODBC | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e1d6f7c6e532622d8bd0ee8fb637754f5df19429
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="the-odbc-cursor-library"></a>Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Блок и Прокручиваемые курсоры являются очень полезные дополнения для многих приложений. Однако не все драйверы поддерживают блок и Прокручиваемые курсоры. Же верно для позиционированного обновления и удаления инструкций и **SQLSetPos**, которые рассматриваются в обновление данных. Таким образом компонент ODBC Windows SDK, ранее включенных в Microsoft данных Access Components (MDAC) пакета SDK, включает библиотеку курсоров. Библиотека курсоров реализует блок, статические курсоры, позиционированные инструкции update и delete, и **SQLSetPos** для любой драйвер, соответствующий уровень соответствия откройте CLI стандартные группы. Библиотека курсоров могут распространяться с приложениями ODBC; соглашение о лицензировании в пакете SDK для получения дополнительной информации см.  
  
 Чтобы использовать библиотеку курсоров, приложение устанавливает атрибут соединения SQL_ATTR_ODBC_CURSORS до подключения к источнику данных. Дополнительные сведения о библиотеке курсоров см. в разделе [библиотека курсоров ODBC приложение F:](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
