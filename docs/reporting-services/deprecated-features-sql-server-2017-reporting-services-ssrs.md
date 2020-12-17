---
title: Нерекомендуемые функции в Reporting Services версии SQL Server 2017 | Документация Майкрософт
description: В этой статье перечислены функции, которые будут объявлены нерекомендуемыми в следующей версии SQL Server Reporting Services.
ms.date: 11/20/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-2017'
ms.openlocfilehash: 553432d2e79069da19eacdd193be9b3b3e7d498c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97425319"
---
# <a name="deprecated-features-in-sql-server-2017-reporting-services"></a>Нерекомендуемые функции в Reporting Services версии SQL Server 2017

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017](../includes/ssrs-appliesto-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

Если функция помечена как нерекомендуемая, это означает следующее.

- Функция находится в режиме обслуживания. В нее не будут вноситься новые изменения, в том числе касающиеся поддержки совместимости с новыми функциями.
- Мы стараемся не удалять нерекомендуемые функции из новых выпусков, чтобы упростить обновление. Однако иногда мы можем окончательно удалять функции из Reporting Services, если они препятствуют дальнейшим инновациям.
- Нерекомендуемые функции нежелательно использовать при разработке новых приложений.

## <a name="features-deprecated-in-the-next-version-of-sql-server"></a>Функции, не рекомендуемые в следующей версии SQL Server

Перечисленные ниже функции Reporting Services версии SQL Server 2017 будут объявлены нерекомендуемыми в следующей версии SQL Server. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в сейчас используются.

> [!NOTE]
> Этот список идентичен списку для Reporting Services версии SQL Server 2016 (13.x). Для Reporting Services версии SQL Server 2017 (14.x) не объявлено о новых нерекомендуемых или неподдерживаемых функциях.


| **Категория** | **Нерекомендуемая функция** | **Замена** |
| --- | --- | --- |
| Сервер отчетов | Отрисовщик HTML 4.0. | Отрисовщик HTML 5 |

## <a name="see-also"></a>См. также раздел

[Неподдерживаемая функциональность в службах SQL Server Reporting Services (SSRS)](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
