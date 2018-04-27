---
title: Начало работы с SSMA для доступа к консоли (AccessToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
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
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abb34d1b0d6656b251c23e209af1f58b9fdb4c6b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Начало работы с SSMA для доступа к консоли (AccessToSQL)
В этом разделе описывается, как запустить и приступить к работе с доступом консольного приложения. Также перечислены в настоящем документе, соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>При запуске консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Последовательно выберите пункты **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для доступа к командной строке** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После консоль успешно запускается в среде Windows, можно выполнить следующие действия для работы с ней:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
2.  [Создание файлов значение переменной &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [Создание файлов подключения сервера &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [Выполнение консоли SSMA &#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](http://msdn.microsoft.com/en-us/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Составление отчетов](http://msdn.microsoft.com/en-us/abb4264a-622e-4215-af5b-14e309b8a399) для просмотра xml подробный вывод отчетов для оценки миграции /conversion и данных. Подробные сведения об ошибке отчеты также можно создать для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли SSMA](../../ssma/access/media/ssmaconsoleoutput.jpg "вывод консоли SSMA")  
  
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
[Установка SQL Server Migration Assistant для Access](http://msdn.microsoft.com/en-us/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)  
  
