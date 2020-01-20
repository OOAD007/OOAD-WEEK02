# การทดลองที่ 2 

## Activity 3 การเขียนโปรแกรมด้วย Win32 API

### วัตถุประสงค์

1. เพื่อให้รู้วิธีการเขียนโปรแกรมบน Windows ด้วยฟังก์ชัน Win32 API
2. เพื่อให้มีความคุ้นเคยกับการใช้เครื่องมือต่างๆ ในการสร้าง Application บน IDE

### ลำดับการทดลอง

1. สร้าง Project ใหม่ ตาม activity ที่ 1
2. คัดลอกไฟล์ .cpp จากการทดลองที่ 2
3. แก้ไข code ในส่วนของการ switch message ให้เป็นดังนี้

``` C++
 ...
 	switch (message) {

 	case WM_PAINT:
 		hdc = BeginPaint (hwnd, &ps);
// 		Ellipse (hdc, 10, 10, 200, 100);
 		EndPaint (hwnd, &ps);
 		return 0;

	case WM_LBUTTONDOWN:
		char str[256];
		POINT pt;   // point of mouse clicked, received via message
		pt.x = LOWORD(lParam);
		pt.y = HIWORD(lParam);
		wsprintf(str,"WM_LBUTTONDOWN\nCo-ordinate are\n (%i, %i)",pt.x,
 			         pt.y);
		MessageBox(hwnd, str, "Left Button Clicked", MB_OK);
		return 0;

	case WM_RBUTTONDOWN:
		pt.x = LOWORD(lParam);
		pt.y = HIWORD(lParam);
		wsprintf(str,"WM_RBUTTONDOWN\nCo-ordinate are\n (%i, %i)",pt.x,
 			         pt.y);
		MessageBox(hwnd, str, "Right Button Clicked", MB_OK);
		return 0;

	case WM_CHAR:
		hdc = GetDC(hwnd);
		TextOut(hdc, 1,1, "  ",3);
		wsprintf(str,"%c",(char) wParam);
		TextOut(hdc, 1,1, str,strlen(str));
		ReleaseDC(hwnd, hdc);
		return 0;

 	case WM_DESTROY:
 		PostQuitMessage (0);
 		return 0;
 	}
...
```

3. กดปุ่ม F5 เพื่อดูผลการทำงานของโปรแกรม

## คำถาม

1. ผลการทำงานของโปรแกรมเป็นอย่างไร ให้ cature หน้าจอพร้อมอธิบายการทำงาน
2. ส่งงานใน repo ตามแนวทางใน activity 1
