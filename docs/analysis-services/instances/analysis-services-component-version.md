---
title: Проверка версии сборки накопительного пакета обновления SQL Server Analysis Services | Документация Майкрософт
ms.date: 07/11/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1da8384bb51360178e1735d13f6c6b706e8b7ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659062"
---
# <a name="verify-analysis-services-cumulative-update-build-version"></a>Проверка версии сборки накопительного пакета обновления служб Analysis Services

Начиная с SQL Server 2017, номер версии сборки службы Analysis Services и номер версии сборки SQL Server Database Engine не совпадают. Хотя службы Analysis Services и компонент Database Engine использует тот же установщик, системы сборки при каждом использовании отделены.

 В некоторых случаях может потребоваться для проверки, если применен пакет сборки накопительного пакета обновления (CU) и были обновлены компоненты служб Analysis Services. Можно проверить, сравнив номера версии сборки файлы компонентов служб Analysis Services, установленных на компьютере с номерами версий сборки для конкретного CU.

## <a name="verify-component-file-version"></a>Проверки версии файла компонента

Для проверки версии файла компонента, 

1. Перейдите к [версии сборок SQL Server 2017](https://support.microsoft.com/help/4047329). 
2. В **сборок SQL Server 2017 накопительное обновление (CU)**, нажмите кнопку **базы знаний** для сборки, вы хотите проверить.
3. В **накопительного обновления (#) для SQL Server 2017** статьи, в **накопительный пакет обновления сведений о пакете** раскройте **сведения о файлах пакета накопительного обновления**.
4. В **SQL Server 2017 Analysis Services** таблицы, проверьте версию файла для **msmdsrv.exe** файл компонента. Если применяется CU, номер версии файла должны соответствовать файл msmdsrv.exe, установленной на компьютере.

## <a name="see-also"></a>См. также  

[Установка обновлений для обслуживания SQL Server](../../database-engine/install-windows/install-sql-server-servicing-updates.md)  

[Центр обновлений для Microsoft SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)
  
  
