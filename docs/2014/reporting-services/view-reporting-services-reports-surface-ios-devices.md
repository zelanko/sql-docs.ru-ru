---
title: Просмотр Reporting Services отчетов на устройствах Microsoft Surface и устройствах Apple iOS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3937f227d025da054a28f73fffde4a57dc365c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098660"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Просмотр отчетов служб Reporting Services на устройствах с Microsoft Surface и Apple iOS
  В этой статье описаны функции и рабочие процессы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , поддерживаемые для планшета Microsoft Surface и устройств с Apple iOS 6 и Apple Safari, таких как iPad.  
  
## <a name="view-and-interact-with-reports"></a>Представление и взаимодействие с помощью отчетов  
 Начиная с версии [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживает просмотр и базовое взаимодействие с отчетами для планшета Microsoft Surface и устройств с браузерами Apple iOS 6 и Apple Safari, таких как iPad. Также можно публиковать отчеты с помощью устройств Microsoft Surface.  
  
 ![Рабочий стол IPad](media/videothumbnail.jpg "Рабочий стол IPad")  
Ознакомьтесь с демонстрацией просмотра отчетов на iPad.  
  
 Можно также просматривать отчеты служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на устройстве Windows Phone 8.  
  
 Чтобы использовать функции, описанные в этом разделе, установите одно из следующего.  
  
-   Для использования сервера отчетов с собственным режимом установите [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] или последующую версию.  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]доступен для загрузки из [центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=35575).  
  
-   Для сервера отчетов в режиме SharePoint установите [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] или более позднюю версию надстройки [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint.  
  
 **Просмотр и взаимодействие с отчетом на устройстве iPad или устройстве Microsoft Surface**  
  
1.  Убедитесь, что можно подключиться к серверу отчетов или сайту SharePoint, где находится отчет.  
  
2.  Откройте отчет, выполнив одно из следующих действий.  
  
    -   **Начать с электронной почты:** В сообщении электронной почты, созданном [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подпиской, выберите URL-адрес отчета. Отчет откроется в браузере.  
  
    -   **Запуск с сервера отчетов:** Просмотрите каталог на сервере [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчетов, а затем выберите имя отчета, чтобы открыть отчет.  
  
    -   **Запуск из библиотеки документов SharePoint:** Перейдите к библиотеке документов SharePoint, содержащей [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты, а затем выберите имя отчета. Можно просматривать отчет и работать с ним.  
  
        > [!IMPORTANT]  
        >  При использовании iPad свойство **Скрытый просмотр** в Safari должно быть отключено.  
  
    -   **Веб-часть SharePoint:** Если веб-часть была добавлена на страницу SharePoint, можно просматривать [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты.  
  
3.  На устройстве Microsoft Surface можно также открыть отчет с использованием диспетчера отчетов. Просмотрите каталог в диспетчере отчетов [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и выберите имя отчета, чтобы открыть его.  
  
    > [!IMPORTANT]  
    >  Просмотр отчетов в диспетчере отчетов не поддерживается на iPad.  
  
4.  Прокручивайте и увеличивайте отчет, выполняя следующее.  
  
    -   Для прокрутки отчета проведите пальцем по экрану (вверх, вниз, влево или вправо). Это жест «скольжение».  
  
    -   Для увеличения установите два пальца на экране и разведите их. Для уменьшения установите два пальца на экране и сведите их. Это жест «щипок».  
  
5.  Переходите и взаимодействуйте с отчетом, выполняя следующее.  
  
    -   Сворачивать и разворачивать элементы отчета, а также строки и столбцы, связанные с группами, можно, нажимая на значок «плюс» (+) для свертывания и «минус» (-) для развертывания.  
  
    -   Переключаться между сортировкой по возрастанию и убыванию для строк в таблице либо строк и столбцов в матрице можно, нажимая кнопку сортировки. Кнопка сортировки обычно находится в заголовке столбца.  
  
    -   Разворачивать и сворачивать область параметров можно, нажимая кнопку со стрелкой в верхней части отчета.  
  
    -   Выбрать значение параметра можно, нажав поле или элемент управления рядом с параметром. Выберите **Просмотр отчета** , чтобы применить значение параметра к отчету.  
  
    -   Для поиска по содержимому отчета щелкните поле рядом с кнопкой **Найти**, введите термин для поиска, а затем нажмите **Найти**.  
  
    -   Для перехода по страницам отчета используйте кнопки навигации или щелкните текстовое поле рядом с кнопками и введите номер страницы.  
  
    -   Для перехода по URL-адресу нажимайте на гиперссылки, добавляемые к таким элементам отчета, как текстовые поля, изображения, диаграммы и датчики.  
  
    -   Для экспорта отчета нажмите значок **раскрывающегося меню экспорта** и выберите формат файла.  
  
        -   Если отчет просматривается на устройстве Microsoft Surface, можно экспортировать отчет в один из следующих форматов.  
  
            -   XML-файл с данными отчета  
  
            -   CSV (с разделителями-запятыми)  
  
            -   PDF  
  
            -   MHTML (веб-архив)  
  
            -   Excel  
  
            -   TIFF  
  
            -   Word  
  
        -   Если отчет просматривается на iPad, отчет можно экспортировать в файл TIFF или PDF.  
  
## <a name="authentication"></a>Аутентификация  
 Проверка подлинности RSWindowsNTLM и RSWindowsBasic работает с [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме и iPad.  
  
 Вообще говоря, рекомендуется использовать RSWindowsBasic в средах, отличных от https, поскольку проверка подлинности этого типа не обеспечивает конфиденциальности при передаче учетных данных.  
  
 Дополнительные сведения о проверке подлинности RSWindowsNTLM и RSWindowsBasic см. в разделе [Authentication with the Report Server](security/authentication-with-the-report-server.md).  
  
## <a name="uploading-reports"></a>Передача отчетов  
 Отчеты с устройства Microsoft Surface можно публиковать с помощью одного из следующих методов, если у вас есть соответствующие разрешения.  
  
> [!IMPORTANT]  
>  Эти методы не поддерживаются на iPad.  
  
-   Передайте файл языка определения отчета (RDL-файл) в библиотеку документов SharePoint. Для этого откройте библиотеку и коснитесь **Передать документ**.  
  
-   Передайте файл определения отчета в базу данных сервера отчетов. Для этого откройте диспетчер отчетов и коснитесь **Передать файл**.  
  
## <a name="additional-information"></a>Дополнительные сведения  
 Дополнительные сведения о службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и поддерживаемых браузерах см. в следующем разделе:  
  
-   [Планирование поддержки Reporting Services и Power View в браузере &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Дополнительные сведения о бизнес-аналитике Microsoft Business Intelligence и мобильных устройствах см. в следующих разделах:  
  
-   [Общие сведения о мобильных устройствах и SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).  
  
-   [Поддерживаемые браузеры мобильных устройств в SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).  
  
-   [Просмотр отчетов и показателей на устройствах Apple iPad (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).  
  
-   [Просмотр отчетов Reporting Services на iPad (видео)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).  
  
-   [Просмотр отчетов служб Reporting Services на устройстве Microsoft Surface RT (видео)](https://technet.microsoft.com/sqlserver/dn146017)  
  
  
