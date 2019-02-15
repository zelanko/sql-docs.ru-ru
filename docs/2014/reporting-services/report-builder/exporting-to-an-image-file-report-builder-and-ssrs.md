---
title: Экспорт в файл изображения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 9d4f3bbc08c4eb2bb24327371593b854788bac85
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56287753"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a>Экспорт в файл изображения (построитель отчетов и службы SSRS)
  Модуль подготовки отчетов изображений преобразует отчет в битовую карту или метафайл. По умолчанию модуль подготовки изображения создает отчет в файле TIFF, который можно просматривать на нескольких страницах. Полученное изображение клиент может просмотреть в программе просмотра изображений и распечатать. В этом разделе содержатся сведения о модуле подготовки изображений и описаны исключения из правил подготовки к просмотру.  
  
 Модуль подготовки изображений создает файлы в форматах, поддерживаемых [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG и TIFF. Если используется формат TIFF, то файлу для главного потока будет присвоено имя *имя_отчета*.tif. Для других форматов, которые формируются по принципу "одна страница в одном файле", файлу будет присвоено имя *имя_отчета_страница.ext* , где *ext* — расширение файла в зависимости от выбранного формата. Чтобы создать файл в другом поддерживаемом формате изображений, укажите в параметре **OutputFormatDeviceInfo** любую из перечисленных выше строк.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="SupportedImageFormats"></a> Поддерживаемые форматы изображения  
 В следующей таблице приведены расширения имени файла и тип MIME для каждого формата модуля подготовки изображений.  
  
|**Тип**|**Расширение**|**MIMEType**|  
|--------------|-------------------|------------------|  
|BMP|BMP|image/bmp|  
|GIF|GIF|image/gif|  
|JPEG|JPEG|image/jpeg|  
|PNG|PNG|image/png|  
|TIFF|tif|image/tiff|  
|EMF|EMF|image/emf|  
|EMFPlus|EMF|image/emf|  
  
  
##  <a name="RenderingMultiplePages"></a> Подготовка к просмотру нескольких страниц  
 TIFF — это единственный формат, который позволяет представлять многостраничные документы в едином файле. Другие форматы, такие как JPG или PNG, выводят по одной странице одновременно и требуют отдельного вызова модуля подготовки отчетов для подготовки к просмотру каждой страницы.  
  
  
##  <a name="Interactivity"></a> Интерактивность  
 Интерактивные возможности не поддерживаются ни одним из форматов изображения, формируемых этим модулем подготовки отчетов. Не обрабатываются следующие интерактивные элементы.  
  
-   Гиперссылки  
  
-   Показать или скрыть  
  
-   Схема документа  
  
-   Ссылки с детализацией или дополнительной информацией  
  
-   Сортировка конечным пользователем  
  
-   Фиксированные заголовки  
  
-   Закладки  
  
  
##  <a name="DeviceInfo"></a> Настройки сведений об устройстве  
 Некоторые параметры по умолчанию для этого модуля подготовки отчетов можно изменить через настройку сведений об устройстве. Дополнительные сведения см. в разделе [Image Device Information Settings](../image-device-information-settings.md).  
  
  
## <a name="see-also"></a>См. также  
 [Разбиение на страницы в службах Reporting Services (построитель отчетов и службы SSRS)](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Интерактивные возможности различных модулей подготовки отчетов к просмотру (построитель отчетов и службы SSRS)](interactive-functionality-different-report-rendering-extensions.md)   
 [Подготовка к просмотру элементов отчета (построитель отчетов и службы SSRS)](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Таблицы, матрицы, списки (построитель отчетов и службы SSRS)](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
