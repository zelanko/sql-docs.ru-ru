---
description: Тестирование ODBC — это приложение с поддержкой ODBC, которое можно использовать для тестирования драйверов ODBC и диспетчера драйверов ODBC.
title: Тестирование ODBC
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC test [ODBC]
- ODBC drivers [ODBC], testing
- gtrtst32.dll
- gtrts32w.dll [ODBC]
- odbct32w.exe [ODBC]
- odbcte32.exe [ODBC]
- testing ODBC drivers [ODBC]
ms.assetid: 7f13894c-5697-436c-be3d-fe16e1a02325
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39869fe1230be75d9a76e13b8ba3938ec31ee5ee
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288249"
---
# <a name="odbc-test"></a>Тестирование ODBC

## <a name="about"></a>Сведения

Microsoft® ODBC Test — это приложение с поддержкой ODBC, которое можно использовать для тестирования драйверов ODBC и диспетчера драйверов ODBC. Тестирование ODBC входит в состав [пакета средств разработки программного обеспечения Microsoft Data Access Components (MDAC) 2,8](https://www.microsoft.com/download/details.aspx?id=21995).

ODBC 3,51 включает версии теста ODBC с поддержкой ANSI и Юникод. Ниже приведены соответствующие файлы.

- `Odbcte32.exe` и `Gtrtst32.dll` для версии ANSI.

- `Odbct32w.exe` и `Gtrts32w.dll` для версии Юникода.

Чтобы использовать тест ODBC, необходимо ознакомиться с API ODBC, языком C и SQL. Дополнительные сведения об API ODBC см. в [справочнике программиста по ODBC](../odbc/reference/odbc-programmer-s-reference.md).

Разделы справки, которые ранее были включены в этот раздел документации, теперь содержатся в программе тестирования ODBC. Откройте `Odbcte32.exe` или `Odbct32w.exe` откройте меню **Справка** и выберите пункт **разделы справки**.

Обратите внимание, что 64-разрядные версии этих приложений, предназначенные для 64-разрядных операционных систем Microsoft Windows, имеют те же имена, что и 32-разрядные версии, даже если они являются отдельными файлами. т. е. имя версии Юникода 64-разрядной версии ODBC — `odbct32w.exe` .

## <a name="open-source"></a>Открытый исходный код

Тест ODBC является открытым исходным кодом. Чтобы просмотреть код и самостоятельно создать последнюю версию теста ODBC, перейдите в [репозиторий GitHub для тестирования ODBC](https://github.com/microsoft/ODBCTest).
