---
title: Фирменная символика на веб-портале | Документы Майкрософт
ms.date: 11/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5f691cee39f88bf8fb0aac54f31239a794b9ac6a
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028733"
---
# <a name="branding-the-web-portal"></a>Фирменная символика на веб-портале

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Вы можете добавить на свой веб-портал элементы фирменного стиля организации. Для этого существуют пакеты фирменной символики. Для работы с пакетами фирменной символики углубленное знание CSS не требуется.  
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/m08kLuofwFA?list=PLv2BtOtLblH3F--8WmK9QcLbx6dV_lVkL" frameborder="0" allowfullscreen></iframe>  
   
## <a name="creating-the-brand-package"></a>Создание пакета фирменной символики
  
Пакет фирменной символики для служб отчетов состоит из трех элементов. Он упаковывается в ZIP-файл.   
  
- color.json  
- metadata.xml  
- logo.png (необязательно)  
  
Файлы должны иметь указанные выше имена. Имя ZIP-файла может быть любым.  
  
### <a name="metadataxml"></a>metadata.xml
  
Файл metadata.xml позволяет присвоить имя пакету фирменной символики, а также содержит ссылки на файлы colors.json и logo.png.  
  
Чтобы изменить имя пакета фирменной символики, измените атрибут **name** для элемента **SystemResourcePackage** .  
  
    name="Multicolored example brand"  
  
В пакет фирменной символики можно включить изображение логотипа (необязательно). Этот элемент описывается в элементе Contents.  
  
Пример без файла логотипа.  
  
    <Contents>  
      <Item key="colors" path="colors.json" />  
    </Contents>  
  
Пример с файлом логотипа.  
  
    <Contents>  
      <Item key="colors" path="colors.json" />  
      <Item key="logo" path="logo.png" />  
    </Contents>  
  
### <a name="colorsjson"></a>Colors.json
  
При загрузке пакета фирменной символики сервер извлекает пары имен и значений из файла colors.json и объединяет их с основной таблицей стилей LESS (brand.less). Затем он обрабатывает этот файл и передает клиенту полученный файл CSS. Все цвета сохраняются в таблице стилей в формате шестисимвольного шестнадцатеричного представления.  
  
Таблица стилей LESS содержит блоки, которые ссылаются на некоторые стандартные переменные LESS, как показано ниже.  
  
    /* primary buttons */   
    .btn-primary {   
        color:@primaryButtonColor;   
        background-color:@primaryButtonBg;   
    }  
  
Синтаксис в целом похож на CSS, но в LESS используется уникальное обозначение цветов с префиксом @symbol. Эти обозначения представляют переменные, значения которых задаются в файле JSON.  
  
Давайте рассмотрим пример файла colors.json со следующими значениями.  
  
    "primary":"#009900",   
    "primaryContrast":"#ffffff"   
  
По результатам обработки выполняется поиск переменной LESS с именем **@primaryButtonBg** , которая сопоставляется со свойством JSON с именем **primary**(в нашем примере это #009900). Результат — вывод допустимых данных CSS.  
  
    .btn-primary {   
        color:#ffffff;   
        background-color:#009900;   
    }  
  
Все основные кнопки будут темно-зелеными с белым текстом.  
  
В файле colors.json для служб отчетов элементы группируются в две основные категории.  
  
- **Interface**: содержит элементы, относящиеся к веб-порталу служб отчетов.  
- **Theme**: содержит элементы, которые относятся к созданным вами мобильным отчетам.  
  
Раздел интерфейса состоит из следующих разделов.  
  
|Раздел|Описание|  
|---|---|  
|primary|Цвета кнопок и цвета при наведении указателя мыши.|  
|Вторичная|Заголовок, панель поиска, меню слева (если отображается) и цвет текста для этих элементов.|  
|Нейтральная основная|Фон области домашней страницы и области отчетов.|  
|Нейтральная вторичная|Фон текстового поля и свойств папки, а также меню настроек.|  
|Нейтральная третичная|Фон параметров сайта.|  
|Сообщения об опасности, предупреждения и сообщения|Цвета для этих сообщений.|  
|Ключевой показатель эффективности|Характеризует цвета как хорошие (1), нейтральные (0), нейтральные (-1) и отсутствующие.|  
  
При первом подключении к серверу с издателем мобильных отчетов и развернутым пакетом фирменной символики тема из этого пакета будет добавлена к списку доступных тем. Вы можете выбирать темы в верхнем правом меню приложения.  
  
![ssRSBrandingMobileReportPublisher](../reporting-services/media/ssrsbrandingmobilereportpublisher.png)  
  
После этого вы сможете использовать тему для любого созданного вами мобильного отчета, даже если он расположен не на том сервере, где развернута тема.   
  
### <a name="using-a-logo"></a>Использование логотипа
  
Если в ваш пакет фирменной символики включено изображение логотипа, оно будет отображаться на веб-портале вместо имени веб-портала, установленного в меню "Параметры сайта".  
  
Файл с изображением логотипа должен иметь формат PNG. Размер файла будет отмасштабирован при отправке на сервер. Полученное изображение будет иметь размер приблизительно 290 x 60 пикселей.  
   
## <a name="applying-the-brand-package-to-the-web-portal"></a>Применение пакета фирменной символики для веб-портала
  
Чтобы добавить, загрузить или удалить пакет фирменной символики:  
  
1.  Щелкните символ **шестеренки** в правом верхнем углу.  
  
2.  Выберите пункт **Настройки сайта**.  
  
    ![ssRSGearMenu](../reporting-services/media/ssrsgearmenu.png)  
  
3.  Выберите раздел **Фирменная символика**.  
  
    ![ssRSBranding](../reporting-services/media/ssrsbranding.png)  
  
**Установленный пакет фирменной символики** : в этом поле будет указано имя пакета, если пакет был передан на сервер, или значение None ("Нет").  
  
**Отправить пакет фирменной символики** : после нажатия этой кнопки пакет будет применен для веб-портала. Это действие выполняется незамедлительно.  
  
Также здесь вы можете **загрузить** или **удалить** пакет. После удаления пакета для веб-портала немедленно восстановится оформление по умолчанию.  
  
## <a name="metadataxml-example"></a>Пример файла metadata.xml
  
    <?xml version="1.0" encoding="utf-8"?>  
    <SystemResourcePackage xmlns="http://schemas.microsoft.com/sqlserver/reporting/2016/01/systemresourcepackagemetadata"  
        type="UniversalBrand"  
        version="2.0.2"  
        name="Multicolored example brand"  
        >  
        <Contents>  
            <Item key="colors" path="colors.json" />  
            <Item key="logo" path="logo.png" />  
        </Contents>  
    </SystemResourcePackage>  
   
## <a name="colorsjson-example"></a>Пример файла colors.json
  
    {  
        "name":"Multicolored example brand",  
        "version":"1.0",  
        "interface":{  
            "primary":"#b31e1e",  
            "primaryAlt":"#ca0806",  
            "primaryAlt2":"#621013",  
            "primaryAlt3":"#e40000",  
            "primaryAlt4":"#e14e50",  
            "primaryContrast":"#fff",  
  
            "secondary":"#042200",  
            "secondaryAlt":"#0f4400",  
            "secondaryAlt2":"#155500",  
            "secondaryAlt3":"#217700",  
            "secondaryContrast":"#49e63c",  
  
            "neutralPrimary":"#d8edff",  
            "neutralPrimaryAlt":"#c9e6ff",  
            "neutralPrimaryAlt2":"#aedaff",  
            "neutralPrimaryAlt3":"#88c8ff",  
            "neutralPrimaryContrast":"#0a2b4c",  
  
            "neutralSecondary":"#e9d8eb",  
            "neutralSecondaryAlt":"#d9badc",  
            "neutralSecondaryAlt2":"#b06cb5",  
            "neutralSecondaryAlt3":"#a75bac",  
            "neutralSecondaryContrast":"#250a26",  
  
            "neutralTertiary":"#f79220",  
            "neutralTertiaryAlt":"#f8a54b",  
            "neutralTertiaryAlt2":"#facc9b",  
            "neutralTertiaryAlt3":"#fce3c7",  
            "neutralTertiaryContrast":"#391d00",  
  
            "danger":"#ff0000",  
            "success":"#00ff00",  
            "warning":"#ff8800",  
            "info":"#00ff",  
            "dangerContrast":"#fff",  
            "successContrast":"#fff",  
            "warningContrast":"#fff",  
            "infoContrast":"#fff",  
  
            "kpiGood":"#4fb443",  
            "kpiBad":"#de061a",  
            "kpiNeutral":"#d9b42c",  
            "kpiNone":"#333",  
            "kpiGoodContrast":"#fff",  
            "kpiBadContrast":"#fff",  
            "kpiNeutralContrast":"#fff",  
            "kpiNoneContrast":"#fff"  
           },  
           "theme":{  
            "dataPoints":[  
                "#0072c6",  
                "#f68c1f",  
                "#269657",  
                "#dd5900",  
                "#5b3573",  
                "#22bdef",  
                "#b4009e",  
                "#008274",  
                "#fdc336",  
                "#ea3c00",  
                "#00188f",  
                "#9f9f9f"  
            ],  
  
            "good":"#85ba00",  
            "bad":"#e90000",  
            "neutral":"#edb327",  
            "none":"#333",  
  
            "background":"#fff",  
            "foreground":"#222",  
            "mapBase":"#00aeef",  
            "panelBackground":"#f6f6f6",  
            "panelForeground":"#222",  
            "panelAccent":"#00aeef",  
            "tableAccent":"#00aeef",  
  
            "altBackground":"#f6f6f6",  
            "altForeground":"#000",  
            "altMapBase":"#f68c1f",  
            "altPanelBackground":"#235378",  
            "altPanelForeground":"#fff",  
            "altPanelAccent":"#fdc336",  
            "altTableAccent":"#fdc336"  
        }  
    }  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
