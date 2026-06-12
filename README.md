# Echtzeit-Objekterkennung mit YOLO

Projekt von Bledar Sllamniku im Kurs Visual Computing (Digital Engineering, B.Sc.; Hochschule München – University of Applied Sciences, SoSe 2026) bei Prof. Dr. Markus Friedrich.

## Über das Projekt

Echtzeit-Objekterkennung ist im Kontext des autonomen Fahrens nicht nur eine akademische, sondern eine sicherheitskritische Anforderung. 
Klassische zweistufige Verfahren wie R-CNN sind zwar präzise, scheitern jedoch an der nötigen Geschwindigkeit. 
YOLO (*You Only Look Once*) begegnet diesem Problem, indem es die Erkennung als ein einziges Regressionsproblem formuliert, d.h. das gesamte Bild wird in einem einzigen Durchgang durch ein neuronales Netz geschickt und liefert alle erkannten Objekte mit Position und Klasse zurück.

Dieses Repository enthält den Quellcode der Projektwebseite zu diesem Thema. 
Die Webseite ordnet die Objekterkennung zunächst in die Visual-Computing-Pipeline ein, behandelt anschließend die theoretischen Grundlagen von YOLO (Grid-System, Bounding Boxes, Confidence Score, Ausgabetensor $7 \times 7 \times 30$) und setzt das Verfahren mit YOLOv8 in Python um. 
Den Abschluss bilden drei interaktive Demos, die direkt im Browser laufen. Hier kann der Leser eigene Bilder und Videos hochladen, den Grid-Mechanismus und Confidence-Schwellwert anpassen sowie die Anwendung als Live-Stream über die eigene Kamera testen.

## Aufruf der Webseite

Die Webseite ist hier erreichbar:

**[https://billys02.github.io/vcde/](https://billys02.github.io/vcde/)**

Eine lokale Installation ist nicht nötig, d.h. sämtliche Inhalte inkl. der interaktiven Demos laufen direkt im Browser.

## Verwendete Technologien

- [Quarto](https://quarto.org/) für die Dokumenterstellung und das Website-Rendering
- [Ultralytics YOLOv8](https://docs.ultralytics.com/) als Modell und Python-API
- [OpenCV](https://opencv.org/) für die Bild- und Videoverarbeitung in Python
- [ONNX Runtime Web](https://onnxruntime.ai/docs/tutorials/web/) v1.21.0 für die Inferenz im Browser
- PyTorch als Backend für YOLOv8

## Hinweis zu den FPS in den Demos

Die in den Demos (Abschnitt 4) erreichbaren Bildraten hängen stark vom verwendeten Browser und der Hardware ab. 

- Mit **Google Chrome oder Edge** auf einem Desktop-Gerät steht meist WebGPU zur Verfügung, was etwa $23$ FPS (Video) bzw. $24-26$ FPS (Webcam) ermöglicht.
- In **Safari** ist die WebGPU-Implementierung bekanntermaßen schwächer und erreicht etwa $10-14$ FPS.
- In **Firefox** oder auf älteren Geräten fällt das System oft auf reines WebAssembly zurück, was nur ca. $3-5$ FPS bedeutet.
- Auf **mobilen Browsern** ist die Performance entsprechend variabel.

Die in der Webseite genannten $45$ FPS bzw. $155$ FPS aus der YOLO-Originalveröffentlichung beziehen sich auf eine GPU-beschleunigte native Ausführung und sind kein Maßstab für die Browser-Demos. 
Für ein optimales Erlebnis wird daher Google Chrome oder Edge auf einem Desktop-Gerät empfohlen.

## Lizenz

Siehe auch [LICENSE](./LICENSE).