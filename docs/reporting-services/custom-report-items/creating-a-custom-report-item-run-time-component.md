---
title: "Создание компонента пользовательского элемента отчета времени выполнения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: c8da0d4ac6024281315dc2e8b0b398904c8a1e6c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="creating-a-custom-report-item-run-time-component"></a>Создание компонента времени выполнения пользовательского элемента отчета
  Реализован в виде компонента пользовательского элемента отчета времени выполнения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] компонента с помощью любого CLS-совместимом языке и вызывается обработчиком отчетов во время выполнения. Свойства компонента времени выполнения в среде разработки задаются настройкой соответствующего компонента времени разработки пользовательского элемента отчета.  
  
 Образец полностью реализованного пользовательского элемента отчета см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="definition-and-instance-objects"></a>Объекты определения и объекты экземпляра  
 Перед реализацией пользовательского элемента отчета важно понимать разницу между *объекты определения* и *объектов экземпляра*. Объекты определения обеспечивают представление пользовательских элементов отчета на языке определения отчетов, а объекты экземпляра являются версиями объектов определения с вычисленными выражениями. У каждого элемента отчета есть только один объект определения. При доступе к свойствам объекта определения, содержащего выражения, возвращается невычисленная строка выражения. Объекты экземпляра содержат вычисленные версии объектов определения и могут находиться в связи «один ко многим» с объектом определения элемента. Например, если в отчете есть область данных <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix>, которая содержит элемент <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> в строке детализации, объект определения будет только один, но у каждой строки в этой области данных будет свой объект экземпляра.  
  
## <a name="implementing-the-icustomreportitem-interface"></a>Реализация интерфейса ICustomReportItem  
 Для создания **CustomReportItem** компонент времени выполнения, необходимо реализовать <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> интерфейс, который определен в динамической библиотеке Microsoft.ReportingServices.ProcessingCore.dll:  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 После реализации интерфейса <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> будут автоматически созданы две заглушки методов: <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> и <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>. Сначала вызывается метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A>. Он используется для задания свойств определения и создания объекта <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image>, в котором будут содержаться свойства определения и свойства экземпляра, необходимые для подготовки к просмотру элемента отчета. Метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> вызывается после вычисления объектов определения и предоставляет объекты экземпляра, которые будут использоваться для подготовки к просмотру элемента отчета.  
  
 Далее следует пример реализации пользовательского элемента отчета, который подготавливает к просмотру имя управляющего элемента в виде изображения.  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Архитектура пользовательского элемента отчета](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [Создание компонента пользовательского элемента отчета времени разработки](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Библиотеки классов элемента пользовательского отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [Как: развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
