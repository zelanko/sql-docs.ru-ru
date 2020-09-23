---
title: Нерекомендуемые функции в Reporting Services версии SQL Server 2019 | Документация Майкрософт
description: В этой статье перечислены функции SQL Server 2019 Reporting Services, которые будут объявлены нерекомендуемыми в следующей версии SQL Server Reporting Services.
ms.date: 08/31/2020
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
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d3e48ab45f34e583dbbeca883a64d04dc965b018
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283821"
---
# <a name="deprecated-features-in-sql-server-2019-reporting-services"></a>Нерекомендуемые функции в Reporting Services версии SQL Server 2019

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2019-and-later](../includes/ssrs-appliesto-2019-and-later.md)] [!INCLUDE [ssrs-appliesto-pbirs](../includes/ssrs-appliesto-pbirs.md)]

Если функция помечена как нерекомендуемая, это означает следующее.

- Функция находится в режиме обслуживания. В нее не будут вноситься новые изменения, в том числе касающиеся поддержки совместимости с новыми функциями.
- Мы стараемся не удалять нерекомендуемые функции из новых выпусков, чтобы упростить обновление. Однако иногда мы можем окончательно удалять функции из Reporting Services, если они препятствуют дальнейшим инновациям.
- Нерекомендуемые функции нежелательно использовать при разработке новых приложений.

**Функции, не рекомендуемые в будущей версии SQL Server**

Служба SQL Server Reporting Services поддерживает приведенные ниже функции в следующей версии SQL Server, но в более поздней версии они станут не рекомендованными. С какой именно версии SQL Server, пока не определено.

| **Категория** | **Нерекомендуемая функция** | **Замена** |
| --- | --- | --- |
| Сервер отчетов | Коллекция элементов отчета | None |
| Сервер отчетов | Мобильные отчеты и издатель мобильных отчетов | Отчеты Power BI на Сервере отчетов Power BI предлагают возможности мобильности. |
| Сервер отчетов | Форматы отображения XLS и DOC | Форматы XLSX and DOCX являются доступными и поддерживаемыми. |
| Сервер отчетов | Atom, веб-канал данных | Поддержка веб-канала данных доступна для общих наборов данных в SSRS и на Сервере отчетов Power BI. |
| Сервер отчетов | Закрепление в Power BI | Теперь служба Power BI непосредственно поддерживает отчеты с разбивкой на страницы.  |

## <a name="see-also"></a>См. также раздел

[Discontinued functionality in SQL Server 2019 Reporting Services (SSRS)](discontinued-functionality-sql-server-reporting-services-2019.md) (Неподдерживаемая функциональность в службах SQL Server 2019 Reporting Services (SSRS))

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
