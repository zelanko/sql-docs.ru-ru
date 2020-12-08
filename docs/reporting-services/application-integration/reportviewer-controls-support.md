---
title: Поддержка версий элемента управления Report Viewer
description: Элемент управления Microsoft Report Viewer совместим со службами SQL Server Reporting Services и сервером отчетов Power BI, к которым применяется современная политика жизненного цикла поддержки.
author: maggiesMSFT
ms.custom: seo-lt-2019
ms.author: maggies
ms.reviewer: jonhp
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 12/01/2020
ms.openlocfilehash: f6c713d579042425dc863b7d4f942229a091d0c4
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96502698"
---
# <a name="support-for-report-viewer-current-branch-versions"></a>Поддержка версий средства просмотра отчетов Сurrent Branch

**_Область применения: Microsoft Report Viewer версии 150.900.148 и выше_**

**Элемент управления Microsoft Report Viewer** совместим со службами SQL Server Reporting Services и сервером отчетов Power BI, к которым применяется современная [политика жизненного цикла поддержки](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy) Майкрософт. Эти сведения относятся как к версиям **ASP.NET**, так и к версиям **WinForms**, распространяемым посредством [NuGet](https://www.nuget.org/). Все выпущенные версии доступны через [NuGet](https://www.nuget.org/). Исправления, компоненты и прочие обновления предоставляются для последней версии. Для получения обновлений требуются последние версии. Для средства просмотра отчетов продолжают выпускаться **обновления для системы безопасности и критические обновления**. Мы уведомляем о любых изменениях в политике поддержки не позднее чем за один год до их внесения.

Журнал версий для элемента управления "Средство просмотра отчетов" доступен по следующим ссылкам:

- [Windows Forms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/)
- [ASP.NET Web Forms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WebForms/)

## <a name="application-server-and-report-server-combinations"></a>Сочетание сервера приложений и сервера отчетов

Некоторые функции элемента управления Report Viewer зависят от стандартного поведения операционной системы. Поэтому для них может требоваться использование одной и той же версии как для клиента (сервер приложений, на котором работает элемент управления Report Viewer), так и для сервера (с Reporting Services). Поддерживаются следующие сочетания сервера приложений и сервера отчетов:

| Сервер приложений | Сервер отчетов |
| :----------------- | :------ |
| Windows Server 2012 | Windows Server 2012 |
| Windows Server 2012 | Windows Server 2012 R2 |
| Windows Server 2012 R2 | Windows Server 2012 R2 |
| Windows Server 2012 R2 | Windows Server 2012 |
| Windows Server 2016 и более поздние версии | Windows Server 2016 и более поздние версии |

## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные сведения об элементе управления Report Viewer см. в статье [Интеграция служб Reporting Services с помощью элементов управления средства просмотра отчетов](integrating-reporting-services-using-reportviewer-controls-get-started.md).
