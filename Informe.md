# Informe Trabajo Final
## Procesamiento de Imágenes
Luciano Valentino Achin Angeles (u202113624)
Daniel Orlando Luis Lázaro (u202021900)
# Introducción

El presente informe detalla el desarrollo de una aplicación de procesamiento de video en tiempo real utilizando técnicas vistas durante el curso. La aplicación permite el acceso a la cámara web y realiza tareas de procesamiento de los frames del video, implementando al menos tres técnicas de procesamiento de imagen.

# Objetivos

-   Desarrollar una aplicación de procesamiento de video en tiempo real: Utilizando Python y bibliotecas como OpenCV y TKinter para capturar y procesar video.
    
-   Implementar tres técnicas de procesamiento de imagen: Aplicar ajustes de brillo, contraste y filtros.
    
-   Evaluar la efectividad de las técnicas implementadas: Analizar cómo las técnicas mejoran o afectan la calidad del video en tiempo real.
    

# Desarrollo

## Selección y Definición del Problema

-   Problema a solucionar: En muchas aplicaciones de videoconferencia y transmisión en vivo, es esencial mejorar la calidad de la imagen en tiempo real para ofrecer una mejor experiencia al usuario. Ajustes inadecuados de brillo, contraste y otros parámetros pueden afectar negativamente la visualización.
    
-   Motivación: Mejorar la calidad de video en tiempo real puede tener un impacto significativo en la experiencia del usuario, especialmente en contextos de videoconferencia donde la claridad visual es crucial.
    
-   Potencial solución: Implementar una aplicación que permita ajustar parámetros como brillo, contraste y aplicar filtros en tiempo real, mejorando la calidad del video capturado por la cámara web.
    

# Aplicación

Para el desarrollo, se utilizó Python junto con la biblioteca OpenCV y TKinter. La aplicación permite el acceso a la cámara web y ofrece una interfaz para ajustar parámetros de brillo, contraste, nitidez, y aplicar diversos filtros en tiempo real.

Desarrollo de la Aplicación:

1.  Captura de Video: Se implementó un método para acceder a la cámara web del dispositivo y capturar el video en tiempo real. Esto es esencial para cualquier aplicación que trabaje con video en directo.
    
2.  Ajustes de Brillo y Contraste: Se añadió funcionalidad para que el usuario pueda modificar el brillo y el contraste del video en tiempo real, utilizando una escala ajustable a través de la interfaz.
    
3.  Filtros de Desenfoque: Se integraron filtros como desenfoque medio y desenfoque bilateral, permitiendo suavizar la imagen y reducir el ruido visual. Estos filtros pueden ser activados o desactivados según la preferencia del usuario.
    
4.  Balance de Color: Se implementaron controles para ajustar el balance de color (rojo, verde y azul), mejorando la representación de colores en el video capturado.
    
5.  Interfaz de Usuario: Se desarrolló una interfaz gráfica sencilla pero funcional que permite a los usuarios ajustar los diferentes parámetros de manera intuitiva. Los controles incluyen deslizadores para brillo, contraste, y balance de color, así como opciones para aplicar filtros de desenfoque.
    

# Conclusiones

El desarrollo de esta aplicación ha permitido explorar diversas técnicas de procesamiento de video en tiempo real y su impacto en la calidad de la imagen. La implementación de ajustes de brillo, contraste, filtros de desenfoque y balance de color proporciona herramientas efectivas para mejorar la visualización del video en contextos donde la claridad y la calidad son esenciales. Adicionalmente, esta aplicación puede ser una base para futuros desarrollos en el ámbito del procesamiento de video en tiempo real, con potenciales aplicaciones en videoconferencias, transmisiones en vivo y otros servicios donde la calidad del video es crucial.# Introducción

El presente informe detalla el desarrollo de una aplicación de procesamiento de video en tiempo real utilizando técnicas vistas durante el curso. La aplicación permite el acceso a la cámara web y realiza tareas de procesamiento de los frames del video, implementando al menos tres técnicas de procesamiento de imagen.

# Objetivos

-   Desarrollar una aplicación de procesamiento de video en tiempo real: Utilizando Python y bibliotecas como OpenCV y TKinter para capturar y procesar video.
    
-   Implementar tres técnicas de procesamiento de imagen: Aplicar ajustes de brillo, contraste y filtros.
    
-   Evaluar la efectividad de las técnicas implementadas: Analizar cómo las técnicas mejoran o afectan la calidad del video en tiempo real.
    

# Desarrollo

## Selección y Definición del Problema

-   Problema a solucionar: En muchas aplicaciones de videoconferencia y transmisión en vivo, es esencial mejorar la calidad de la imagen en tiempo real para ofrecer una mejor experiencia al usuario. Ajustes inadecuados de brillo, contraste y otros parámetros pueden afectar negativamente la visualización.
    
-   Motivación: Mejorar la calidad de video en tiempo real puede tener un impacto significativo en la experiencia del usuario, especialmente en contextos de videoconferencia donde la claridad visual es crucial.
    
-   Potencial solución: Implementar una aplicación que permita ajustar parámetros como brillo, contraste y aplicar filtros en tiempo real, mejorando la calidad del video capturado por la cámara web.
    

# Aplicación

Para el desarrollo, se utilizó Python junto con la biblioteca OpenCV y TKinter. La aplicación permite el acceso a la cámara web y ofrece una interfaz para ajustar parámetros de brillo, contraste, nitidez, y aplicar diversos filtros en tiempo real.

Desarrollo de la Aplicación:

1.  Captura de Video: Se implementó un método para acceder a la cámara web del dispositivo y capturar el video en tiempo real. Esto es esencial para cualquier aplicación que trabaje con video en directo.
    
2.  Ajustes de Brillo y Contraste: Se añadió funcionalidad para que el usuario pueda modificar el brillo y el contraste del video en tiempo real, utilizando una escala ajustable a través de la interfaz.
    
3.  Filtros de Desenfoque: Se integraron filtros como desenfoque medio y desenfoque bilateral, permitiendo suavizar la imagen y reducir el ruido visual. Estos filtros pueden ser activados o desactivados según la preferencia del usuario.
    
4.  Balance de Color: Se implementaron controles para ajustar el balance de color (rojo, verde y azul), mejorando la representación de colores en el video capturado.
    
5.  Interfaz de Usuario: Se desarrolló una interfaz gráfica sencilla pero funcional que permite a los usuarios ajustar los diferentes parámetros de manera intuitiva. Los controles incluyen deslizadores para brillo, contraste, y balance de color, así como opciones para aplicar filtros de desenfoque.

## Código
    
    import cv2
    import numpy as np
    from tkinter import *
    from tkinter import ttk
    from datetime import datetime
    from PIL import Image, ImageTk
    
    def ajusteBrillo(img, brightness=50):
        return cv2.convertScaleAbs(img, alpha=brightness/50)
    
    def ajusteContraste(img, contrast=50):
        return cv2.convertScaleAbs(img, beta=contrast)
    
    def ajusteNitidez(img, sharpness=50):
        kernel = np.array([[0, -1, 0],
                           [-1, 5 + sharpness / 50, -1],
                           [0, -1, 0]])
        return cv2.filter2D(img, -1, kernel)
    
    def aplicaLaplaciano(img):
        return cv2.Laplacian(img, cv2.CV_8U)
    
    def aplicaGaussianBlur(img, size=5):
        if size % 2 == 0:
            size += 1
        return cv2.GaussianBlur(img, (size, size), 0)
    
    def cambioTono(img, hue=0):
        if len(img.shape) == 3 and img.shape[2] == 3:
            hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
            hsv[:, :, 0] = (hsv[:, :, 0] + hue) % 180
            img = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)
        return img
    
    def cambioSaturacion(img, saturation=0):
        if len(img.shape) == 3 and img.shape[2] == 3:
            hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
            hsv[:, :, 1] = np.clip(hsv[:, :, 1] + saturation, 0, 255)
            img = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)
        return img
    
    def aberracionCromatica(img):
        if len(img.shape) == 3 and img.shape[2] == 3:
            b, g, r = cv2.split(img)
            b = cv2.GaussianBlur(b, (5,5), 5)
            g = cv2.GaussianBlur(g, (3,3), 3)
            r = cv2.GaussianBlur(r, (7,7), 1)
            img = cv2.merge([b, g, r])
        return img
    
    def suavizadoConservativo(img):
        kernel = np.ones((5, 5), np.uint8)
        erosion = cv2.erode(img, kernel, iterations=1)
        img = cv2.dilate(erosion, kernel, iterations=1)
        return img
    
    def deteccionBordes(img):
        return cv2.Canny(img, 100, 200)
    
    def aplicaSepia(img):
        if len(img.shape) == 3 and img.shape[2] == 3:
            kernel = np.array([[0.272, 0.534, 0.131],
                               [0.349, 0.686, 0.168],
                               [0.393, 0.769, 0.189]])
            img = cv2.transform(img, kernel)
        return img
    
    def mediaBlur(img, size=5):
        if size % 2 == 0:
            size += 1
        return cv2.blur(img, (size, size))
    
    def medianaBlur(img, size=5):
        if size % 2 == 0:
            size += 1
        return cv2.medianBlur(img, size)
    
    def filtroBilateral(img, d=9, sigma_color=75, sigma_space=75):
        return cv2.bilateralFilter(img, d, sigma_color, sigma_space)
    
    def escalaGrises(img):
        return cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    
    def convierteNegativo(img):
        return cv2.bitwise_not(img)
    
    def balanceColor(img, r=1.0, g=1.0, b=1.0):
        img = img.astype(np.float32)
        img[:,:,2] *= r
        img[:,:,1] *= g
        img[:,:,0] *= b
        return np.clip(img, 0, 255).astype(np.uint8)
    
    def filtroSobel(img):
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        grad_x = cv2.Sobel(gray, cv2.CV_16S, 1, 0)
        grad_y = cv2.Sobel(gray, cv2.CV_16S, 0, 1)
        abs_grad_x = cv2.convertScaleAbs(grad_x)
        abs_grad_y = cv2.convertScaleAbs(grad_y)
        return cv2.addWeighted(abs_grad_x, 0.5, abs_grad_y, 0.5, 0)
    
    def filtroRoberts(img):
        kernel_x = np.array([[1, 0], [0, -1]], dtype=int)
        kernel_y = np.array([[0, 1], [-1, 0]], dtype=int)
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        img_x = cv2.filter2D(gray, cv2.CV_16S, kernel_x)
        img_y = cv2.filter2D(gray, cv2.CV_16S, kernel_y)
        abs_x = cv2.convertScaleAbs(img_x)
        abs_y = cv2.convertScaleAbs(img_y)
        return cv2.addWeighted(abs_x, 0.5, abs_y, 0.5, 0)
    
    def actualizaImagen():
        global frame
        frame = cap.read()[1]
    
        brightness = brightness_scale.get()
        contrast = contrast_scale.get()
        sharpness = sharpness_scale.get()
        blur = blur_scale.get()
        hue = hue_scale.get()
        saturation = saturation_scale.get()
        mean_blur = mean_blur_scale.get()
        median_blur = median_blur_scale.get()
        bilateral_filter = bilateral_filter_scale.get()
        red_balance = red_scale.get() / 50
        green_balance = green_scale.get() / 50
        blue_balance = blue_scale.get() / 50
        
        frame = ajusteBrillo(frame, brightness)
        frame = ajusteContraste(frame, contrast)
        frame = ajusteNitidez(frame, sharpness)
        frame = cambioTono(frame, hue)
        frame = cambioSaturacion(frame, saturation)
        frame = balanceColor(frame, red_balance, green_balance, blue_balance)
    
        if blur > 1:
            frame = aplicaGaussianBlur(frame, blur)
        if mean_blur > 1:
            frame = mediaBlur(frame, mean_blur)
        if median_blur > 1:
            frame = medianaBlur(frame, median_blur)
        if bilateral_filter > 1:
            frame = filtroBilateral(frame, bilateral_filter)
    
        filter_selected = filter_var.get()
        if filter_selected == "Laplacian":
            frame = aplicaLaplaciano(frame)
        elif filter_selected == "Edge Detection":
            frame = deteccionBordes(frame)
        elif filter_selected == "Sepia":
            frame = aplicaSepia(frame)
        elif filter_selected == "Chromatic Aberration":
            frame = aberracionCromatica(frame)
        elif filter_selected == "Conservative Smoothing":
            frame = suavizadoConservativo(frame)
        elif filter_selected == "Grayscale":
            frame = escalaGrises(frame)
        elif filter_selected == "Negative":
            frame = convierteNegativo(frame)
        elif filter_selected == "Sobel":
            frame = filtroSobel(frame)
        elif filter_selected == "Roberts":
            frame = filtroRoberts(frame)
    
        img = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
        img = cv2.resize(img, (640, 480))
        img = Image.fromarray(img)
        img = ImageTk.PhotoImage(image=img)
        image_label.config(image=img)
        image_label.image = img
        root.after(10, actualizaImagen)
        
    
    def tomarFoto():
        global frame
        now = datetime.now()
        timestamp = now.strftime("%Y%m%d_%H%M%S")
        filename = f"img_{timestamp}.png"
        cv2.imwrite(filename, frame)
    
    def botonCircular(canvas, x, y, radius, color, border_color, command):
        circle_inner = canvas.create_oval(x - radius, y - radius, x + radius+8, y + radius+8, fill=color, outline=border_color, width=3)
        circle_inner = canvas.create_oval(x - radius, y - radius, x + radius+5, y + radius+5, fill='black', outline='black', width=3)
        circle_inner = canvas.create_oval(x - radius, y - radius, x + radius, y + radius, fill=color, outline=border_color, width=3)
    
        canvas.tag_bind(circle_inner, '<Button-1>', lambda event: command())
        return circle_inner
    
    cap = cv2.VideoCapture(0)
    root = Tk()
    root.title("Filtro de Imagen en Tiempo Real")
    
    main_frame = Frame(root, bg='black')
    main_frame.pack(pady=(50,50))
    
    image_label = Label(main_frame, bg='black', pady=50)
    image_label.grid(row=0, column=0, columnspan=15)
    
    control_frame = Frame(root, bg='black')
    control_frame.pack(pady=10)
    button_frame = Frame(root, bg='black')
    button_frame.pack(side=BOTTOM, fill=X)
    
    #Brillo
    Label(control_frame, text="Brightness", fg='white', bg='black').grid(row=1, column=0)
    brightness_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    brightness_scale.set(50)
    brightness_scale.grid(row=1, column=1)
    
    #Contraste
    Label(control_frame, text="Contrast", fg='white', bg='black').grid(row=1, column=2)
    contrast_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    contrast_scale.set(50)
    contrast_scale.grid(row=1, column=3)
    
    #Nitidez
    Label(control_frame, text="Sharpness", fg='white', bg='black').grid(row=1, column=4)
    sharpness_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    sharpness_scale.set(50)
    sharpness_scale.grid(row=1, column=5)
    
    #Blur
    Label(control_frame, text="Blur", fg='white', bg='black').grid(row=1, column=6)
    blur_scale = Scale(control_frame, from_=1, to=20, orient=HORIZONTAL, bg='black', fg='white')
    blur_scale.set(1)
    blur_scale.grid(row=1, column=7)
    
    #Tono
    Label(control_frame, text="Hue", fg='white', bg='black').grid(row=1, column=8)
    hue_scale = Scale(control_frame, from_=0, to=180, orient=HORIZONTAL, bg='black', fg='white')
    hue_scale.set(0)
    hue_scale.grid(row=1, column=9)
    
    #Saturación
    Label(control_frame, text="Saturation", fg='white', bg='black').grid(row=1, column=10)
    saturation_scale = Scale(control_frame, from_=0, to=255, orient=HORIZONTAL, bg='black', fg='white')
    saturation_scale.set(0)
    saturation_scale.grid(row=1, column=11)
    
    #Media Blur
    Label(control_frame, text="Mean Blur", fg='white', bg='black').grid(row=1, column=12)
    mean_blur_scale = Scale(control_frame, from_=1, to=20, orient=HORIZONTAL, bg='black', fg='white')
    mean_blur_scale.set(1)
    mean_blur_scale.grid(row=1, column=13)
    
    #Mediana Blur
    Label(control_frame, text="Median Blur", fg='white', bg='black').grid(row=2, column=0)
    median_blur_scale = Scale(control_frame, from_=1, to=20, orient=HORIZONTAL, bg='black', fg='white')
    median_blur_scale.set(1)
    median_blur_scale.grid(row=2, column=1)
    
    # Filtro Bilateral
    Label(control_frame, text="Bilateral Filter", fg='white', bg='black').grid(row=2, column=2)
    bilateral_filter_scale = Scale(control_frame, from_=1, to=20, orient=HORIZONTAL, bg='black', fg='white')
    bilateral_filter_scale.set(1)
    bilateral_filter_scale.grid(row=2, column=3)
    
    #Balance Rojo
    Label(control_frame, text="Red Balance", fg='white', bg='black').grid(row=2, column=4)
    red_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    red_scale.set(50)
    red_scale.grid(row=2, column=5)
    
    #Balance Verde
    Label(control_frame, text="Green Balance", fg='white', bg='black').grid(row=2, column=6)
    green_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    green_scale.set(50)
    green_scale.grid(row=2, column=7)
    
    #Balance Azul
    Label(control_frame, text="Blue Balance", fg='white', bg='black').grid(row=2, column=8)
    blue_scale = Scale(control_frame, from_=0, to=100, orient=HORIZONTAL, bg='black', fg='white')
    blue_scale.set(50)
    blue_scale.grid(row=2, column=9)
    
    #Seleccion de Filtros
    Label(control_frame, text="Filter", fg='white', bg='black').grid(row=2, column=10)
    filter_var = StringVar(control_frame)
    filter_var.set("None")
    filter_menu = ttk.Combobox(control_frame, textvariable=filter_var, width=15)
    filter_menu['values'] = ["None", "Laplacian", "Edge Detection", "Sepia", "Chromatic Aberration",
                             "Conservative Smoothing", "Grayscale", "Negative", "Sobel", "Roberts"]
    filter_menu.grid(row=2, column=11)
    
    #Botón de tomar foto
    canvas = Canvas(root, width=100, height=100, bg='black', highlightthickness=0)
    canvas.pack(pady=(50,50))
    button_radius = 30
    button_x = 50
    button_y = 50
    button_color = 'white'
    button_border_color = 'white'
    circle_button = botonCircular(canvas, button_x, button_y, button_radius, button_color, button_border_color, tomarFoto)
    
    actualizaImagen()
    root.configure(bg='black')
    root.mainloop()
    
    cap.release()
    cv2.destroyAllWindows()
    

# Conclusiones

El desarrollo de esta aplicación ha permitido explorar diversas técnicas de procesamiento de video en tiempo real y su impacto en la calidad de la imagen. La implementación de ajustes de brillo, contraste, filtros de desenfoque y balance de color proporciona herramientas efectivas para mejorar la visualización del video en contextos donde la claridad y la calidad son esenciales. Adicionalmente, esta aplicación puede ser una base para futuros desarrollos en el ámbito del procesamiento de video en tiempo real, con potenciales aplicaciones en videoconferencias, transmisiones en vivo y otros servicios donde la calidad del video es crucial.
