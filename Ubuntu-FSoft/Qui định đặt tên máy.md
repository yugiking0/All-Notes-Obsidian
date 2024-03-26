
# **QUY ĐỊNH** **ĐẶT COMPUTER NAME CHO CÁC THIẾT BỊ TRONG CÔNG TY**

### **3.2. Helpdesk**

#### 3.2.1. **Set Computername**

##### 3.2.1.1. **Với các máy tính có join domain và không join domain: (Áp dụng cho các máy PC, Laptop, server, test, ảo hóa…)**

Format: **Tên chữ cái***Mã nhân viên*==ký tự nhận biết số lần cài==(Maximum là 15 ký tự)

Syntax: **Alphabet***Employee ID*==Alphabet==

Tên chữ cái: Được định nghĩa bao gồm 3 ký tự chữ cái.

Mã nhân viên: Tương ứng với mã nhân viên gồm 8 số.

ký tự nhận biết số lần cài: Tương ứng với việc cài mới, cài lại, thay đổi môi trường…

Dựa vào các qui tắc trên, ta có các vd như sau:

- User DungBA có sử dụng PC để làm môi trường Production. PC sẽ được đặt tên máy như sau:

 **CPP00000871A**

- User DungBA có sử dụng PC để làm môi trường Test. PC sẽ được đặt tên máy như sau:

 **CPT00000871A**

 Tương tự với trường hợp user sử dụng laptop và server. 

##### 3.2.1.2. **Với các máy tính cài cho day-one: (Áp dụng cho các máy PC, Laptop)** 

Format: CPPAccount (Maximum là 15 ký tự).

Syntax: CPPAccount

CPP: Được định nghĩa bao gồm 3 ký tự chữ cái.

Account: Account được cấp cho nhân viên mới.

Dựa vào các qui tắc trên, ta có các vd như sau:

- User Bùi Anh Dũng join vào Fsoft và được tạo account là DungBA. Vì vậy tên máy sẽ được đặt thành:

 **CPPDUNGBA**

##### 3.2.1.3. **Với các máy tính sử dụng với mục đích dùng chung, dùng ảo hóa trên PC của user.**

Format: Ký tự nhận biết mục đích sử dụngBarcode (Maximum là 15 ký tự)

Syntax: CharactersBarcode

ký tự nhận biết mục đích sử dụng: Tương ứng với việc user dùng máy với mục đích gì.

Barcode: Mã tài sản.

 Dựa vào các qui tắc trên, ta có các vd như sau:

- User DungBA có sử dụng PC để phục vụ cho việc họp hành. PC sẽ được đặt tên máy như sau:

**MT-CA025996 (PC Meeting)**

- User DungBA có sử dụng máy ảo trên PC để làm môi trường Test. Máy ảo sẽ được đặt tên máy như sau:

**VM-CA025996 (PC Virtual)**

- User DungBA có sử dụng PC để làm máy in. Máy in sẽ được đặt tên máy như sau:

   **PR-CA025996 (PC Printer)**

##### 3.2.1.4. **Quy định về đặt tên máy cho các lớp training**

**a. PC (Or all kinds of PCs are located inside of class room)**

Format: Tên lớp-Số thứ tự-Barcode (Maximum là 15 ký tự).

Syntax: [Tên lớp]-[Number]-[Barcode]

Tên lớp (Required):  Tương ứng với tên của lớp học

Số thứ tự (Optional):  Được bắt đầu từ chữ cái V và đánh số từ 01 đến 99 tương ứng với số lượng máy trong lớp học.

Barcode: Mã tài sản.

Dựa vào các qui tắc trên, ta có các vd như sau:

- User thuộc lớp fresher sử dụng PC trong lớp học tại HN. PC sẽ được đánh số như sau:

**Cl-01****-CA025996*

**Cl-02****-CA025996*

**Cl-03****-CA025996*

**b.** **VMs (Or all kinds of VDI are located inside of class room)**

Format: Tên lớp-Số thứ tự-Barcode (Maximum là 15 ký tự).

Syntax: [Tên lớp]-[Number]-[Barcode]

Tên lớp (Required):  Tương ứng với tên của lớp học.

Số thứ tự (Optional):  Được bắt đầu từ chữ cái V và đánh số từ 01 đến 99 tương ứng với số lượng máy trong lớp học.

Barcode: Mã tài sản

Dựa vào các qui tắc trên, ta có các vd như sau:

- User thuộc lớp fresher sử dụng PC trong lớp học. PC sẽ được đánh số như sau:

**Cl-V1****-CA025996**

**Cl-V2****-CA025996**

**Cl-V3****-CA025996**

3.2.1.5. **Quy định về đặt tên cho các máy WFH**

(Áp dụng cho các PC, Laptop user mang về nhà làm việc).

Format: WFH-Barcode (Maximum là 15 ký tự).

WFH:  Work from home. 

Barcode: Barcode dựa trên tem tài sản của thiết bị.

Dựa vào các qui tắc trên, ta có các vd như sau:

- User DungBA có mươn 1 PC có Barcode là 025996 để về nhà làm việc thì computer name sẽ được đặt như sau:

**WFH-CA025996**

- User DungBA có mươn 1 laptop có Barcode là 025996 để về nhà làm việc thì computer name sẽ được đặt như sau:

**WFH-LAP025996**

3.2.1.6  **Quy định về đặt tên cho các máy tính sử dụng với mục đích Terminal**.

    (Áp dụng cho các PC, Laptop, Thin Client sử dụng với mục đích terminal).

Format: Term-Barcode (Maximum là 15 ký tự).
Barcode: Barcode dựa trên tem tài sản của thiết bị.
Dựa vào các qui tắc trên, ta có các vd như sau:

- User DungBA được cấp 1 PC có Barcode là 025996 để sử dụng cho mục đích terminal thì computer name sẽ được đặt như sau:

**Term-CA025996**

- User DungBA được cấp 1 Laptop có Barcode là 025996 để sử dụng cho mục đích terminal thì computer name sẽ được đặt như sau:

**Term-LAP025996**

- User DungBA được cấp 1 Thin Client có Barcode là 025996 để sử dụng cho mục đích terminal thì computer name sẽ được đặt như sau:

**Term-Thin025996**