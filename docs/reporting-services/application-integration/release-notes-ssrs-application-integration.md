---
title: Заметки о выпуске элементов управления средства просмотра отчетов SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maghan
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 1528358c8aff5d6e99869f0f4f8c1676ee2d5e75
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730905"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Заметки о выпуске для элементов управления средства просмотра отчетов для веб-форм и WinForms служб SSRS

Это заметки о выпуске для элементов управления средства просмотра отчетов, веб-форм и WinForms, связанные с [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Заметки о выпуске для SSRS, см. в разделе [заметки о выпуске для SQL Server Reporting Services (SSRS) 2017 и более поздние версии](../release-notes-reporting-services.md).

## <a name="15013580"></a>150.1358.0
| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправления ошибок | Откат изменений, удален Microsoft.ReportViewer.Design сборки из ссылок проекта. |
|           | В рамках других изменений две сборки были изменены с 15,0 версии 15.3. Это были отменены. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправления ошибок  | Правильное предварительного просмотра печати высокого разрешения ЭКРАНА монитора |
|            | Диалоговое окно печати будут отображаться за пределами видимого пространства |
|            | Большое количество параметров привело к параметр полосы прокрутки и раскрывающиеся списки не работает надлежащим образом |
|            | Исправлена проблема с параметрами времени значение Null, а также даты |
|            | JQuery, обновленные до версии 3.3.1 |
|            | Исправлена перекрытия с ячейках табликса при подготовке к просмотру HTML |
|            | Удалить время разработки, чтобы исключить ошибочные сборки VS, добавляемый в проекты ссылки проекта |
|            | Исправлена ошибка специальных возможностей панели инструментов описывать только для активных элементов |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправлены ошибки, препятствующие загрузке отчетов без параметров через **Server.LoadReportDefinition**. | &nbsp; |
| Элемент управления средства просмотра отчетов WebForms. | Поддерживает внедрение на страницах с написанием справа налево (на страницах, которые изменяют поток текста с помощью свойства CSS *direction: rtl;* ).<br/><br/>Поддерживает настройку печатного текста в диалоговом окне с помощью интерфейса локализации *IReportViewerMessages5*.<br/><br/>Улучшена поддержка специальных возможностей.<br/><br/>&bull; &nbsp; &nbsp; [Пакет NuGet для элемента управления средства просмотра отчетов из веб-форм](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Элемент управления средства просмотра отчетов WinForms. | Исправлены ошибки при печати, когда приложение выполняется в режиме высокого разрешения.<br/><br/>&bull; &nbsp; &nbsp; [Пакет NuGet для WinForms управления средства просмотра отчетов](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Следующие шаги

[Начало работы](integrating-reporting-services-using-reportviewer-controls-get-started.md) с элементами управления средства просмотра отчетов.

Остались вопросы? [Посетите форум Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
