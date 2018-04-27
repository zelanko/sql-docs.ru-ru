---
title: Начало работы с SSMA для DB2 консоли (DB2ToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f245c017-023e-4880-8721-8908d339525e
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f08cd6468fc5e18ed0e262c803d405cb3bd86050
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Начало работы с SSMA для DB2 консоли (DB2ToSQL)
В этом разделе описывается, как запустить и приступить к работе с DB2 консольного приложения. Также перечислены в настоящем документе, соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>При запуске консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Последовательно выберите пункты **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] помощник по миграции для DB2 командной строки** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После консоль успешно запускается в среде Windows, можно выполнить следующие действия для работы с ней:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Создание файлов значение переменной &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Создание файлов подключения сервера &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [Выполнение консоли SSMA &#40;DB2ToSQL&#41; ](../../ssma/db2/executing-the-ssma-console-db2tosql.md) зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Управление паролями](http://msdn.microsoft.com/en-us/56d546e3-8747-4169-aace-693302667e94) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Создание отчетов](http://msdn.microsoft.com/en-us/69ef5fd9-190d-4c58-8199-b3f77d5e1883) для просмотра xml подробный вывод отчетов для оценки миграции /conversion и данных. Подробные сведения об ошибке отчеты также можно создать для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли ssma_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "консоли ssma_oracle")  
  
Интерпретация цветовой выходные данные в консоли в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Метка даты и времени, сообщение для пользователя|  
|White|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для DB2](http://msdn.microsoft.com/en-us/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
