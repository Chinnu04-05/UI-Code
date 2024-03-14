import cv2 
import numpy as np

cap = cv2.VideoCapture(0)
canvas = np.ones((480, 640, 3), dtype="uint8") * 125 # air canvas

while True:
    ret, frame = cap.read()
    
    if not ret:
        break 

    # flip the camera horizontal 
    frame = cv2.flip(frame, 1) 

    # green box
    cv2.rectangle(frame, (50, 50), (175, 150), (0, 255, 0), -1)
    cv2.putText(frame, "Green", (90, 100), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color=(0, 0, 0), thickness=1)

    # blue box
    cv2.rectangle(frame, (200, 50), (325, 150), (255, 0 , 0), -1)
    cv2.putText(frame, "blue", (245, 100), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color=(0, 0, 0), thickness=1)

    # red box
    cv2.rectangle(frame, (350, 50), (475, 150), (0, 0, 255), -1)
    cv2.putText(frame, "Red", (400, 100), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color=(0, 0, 0), thickness=1)

    # save button 
    cv2.rectangle(frame, (475, 375), (600, 450), (255, 255, 255), -1)
    cv2.putText(frame, "save", (525, 425), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color=(0, 0, 0), thickness=1)

    cv2.imshow("Frame", frame)
    cv2.imshow("Air Canvas", canvas)

    key = cv2.waitKey(1)
    if key == 27:
        break

cap.release()
cv2.destroyAllWindows()
