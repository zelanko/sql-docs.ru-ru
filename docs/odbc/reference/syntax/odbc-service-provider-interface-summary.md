---
title: Резюме интерфейса поставщика услуг ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2f7e459cc7b89106bf1b7ebcd49c699d43da9f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298901"
---
# <a name="odbc-service-provider-interface-summary"></a>Сводка по интерфейсу поставщика служб ODBC
В следующей таблице описаны функции интерфейса интерфейса поставщика услуг ODBC. Для получения дополнительной информации о синтаксисе и семантике для каждой функции, [см.](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)  
  
|Имя функции|Цель|  
|-------------------|-------------|  
|[СЗЛСетКоннекаттаттПродбИнФО](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|То же самое, что [и s'LSetConnectAttr,](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)но он устанавливает атрибут на маркере информации соединения, а не на ручке соединения.|  
|[СЗЛСетДрайверКоннинфо](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Устанавливает строку соединения в токен информации о подключении для вызова [приложения S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|[СЗЛСетКоннекинфо](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Устанавливает источник данных, идентификатор пользователя и пароль в токен информации о подключении для вызова [приложения S'LConnect.](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|[СЗЛГетПулИД](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Извлекает идентификатор пула.|  
|[Соединение СЗЛРатЕ](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Определяет, может ли драйвер повторно использовать существующее соединение в пуле соединения.|  
|[СЗЛПулКоннект](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Создайте новое соединение, если соединение в пуле не может быть использовано повторно.|  
|[СЗЛКCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Сообщает водителю, что идентификатор пула был приурочен.|
