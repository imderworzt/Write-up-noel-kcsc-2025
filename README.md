# Write-up-noel-kcsc-2025

## Part 1: Bài viết và sự khởi đầu

<img width="682" height="535" alt="image" src="https://github.com/user-attachments/assets/324153f9-c1e6-4e96-827c-8da5c81386aa" />

Từ bài viết này, ta rút ra cụm từ 𝐂𝐡𝐫𝐢𝐬𝐭𝐦𝐚𝐬𝐊𝐢𝐝-𝟐𝟎𝟐𝟓

Tìm trên Youtube chúng ta sẽ ra:

<img width="1700" height="1003" alt="image" src="https://github.com/user-attachments/assets/d57f8109-291b-4588-9965-418013dc5fce" />


Thấy có 1 danh sách phát, với một Vid bị ẩn

Sử dụng Wayback Machine, chúng ta tìm được:

<img width="750" height="81" alt="image" src="https://github.com/user-attachments/assets/45ef044a-0996-4a5e-8f07-4f3c3b052903" />

KCSC{cHuC_C4c_b4n

## Part 2: Mối nghi ngờ ban đầu và đoạn video

Ban đầu, mình đã nghi ngờ sẽ có gì đó trong phần đánh giá của trường ở Google Map (cái này sẽ còn nói ở phần cuối)

Ở ảnh trước, ngoài part 1 ra còn một đoạn mã, giải mã base 64 sẽ ra một link cybersharing

Xem video trong link này sẽ thấy rất bình thường, cho đến khi chúng ta xem review mới thứ 2 về trường:

<img width="409" height="476" alt="image" src="https://github.com/user-attachments/assets/213ff6a3-fb5d-4e61-893f-40d885ac4eea" />

<img width="1919" height="998" alt="image" src="https://github.com/user-attachments/assets/2f6a6d2b-82ba-4476-a26b-26b916cef735" />

Vâng, nó là một giọt nước

_614n6_51nh_Vu1

## Part 3: Lại là GitHub

Tra tên người dùng: Kchristmas8386 trên các công cụ tìm kiếm, ta tìm được 1 link Github

<img width="1919" height="1001" alt="image" src="https://github.com/user-attachments/assets/78e67c68-c006-43d2-a8b8-f06bdd50ba79" />

Ta thấy có 4 commit, xem commit:

<img width="1234" height="127" alt="image" src="https://github.com/user-attachments/assets/c6a5ce32-5fb9-4999-b42d-dd2cfb0068cb" />

Ta chú ý đến 2 commit này:

<img width="1246" height="120" alt="image" src="https://github.com/user-attachments/assets/0f9cce36-e16a-4544-a0c5-94a6297080c4" />

Kiểm tra phần bên dưới, ta có:

<img width="659" height="412" alt="image" src="https://github.com/user-attachments/assets/aebbf23b-4714-40e3-befb-b83551ed7440" />

_v3_l3u_l3U_m4y_b4n

## Part 4: Thành phố mang tên Bác và cánh cửa đến phần cuối cùng:

Quay lại phần trước, chúng ta còn có được:

<img width="1582" height="154" alt="image" src="https://github.com/user-attachments/assets/126ffe17-ea88-496e-b6fa-87eedb71a323" />

Viết đoạn mã sau để decrypt:

```
def solve_puzzle():
    # The hex output provided
    hex_data = "002a717034333a205776b3c7f868b66baf2fdc5f6d342957623463506172044c52534e2b134b2b42470d2ba71b7c764582ab884d1b4187cabe5b0d1a776a8a3dfd90b91c3a7325fde570de414c56ad3de3789338db14d2df3adad5434be2f124676674b48feb15fee8061e4a4fbfde24b2424253f934523606ad37aeafee3e4a3f2a9701f8a3c000130a21beb1777e3d1899c22f491b3d0a3dfd06cda4e5ce6da037c0c8e2e9b1cc4af7bd4a3680643c303b6c3305146c36665f76346e506972f4b8a761e36bb52fd66c33750f643355526d10795f62346e5061527420333a205f7643330d5a1b2b094b2171194c0d5562146e5061727421332220b7341ae5c442a95e611cbbf5c445a55e60e2a61dc603a8216371255976335f6c32755e6c6c555f6d80795f62346e"

    # The key found in the original source code
    key = "Part 3: _v3_l3u_l3U_m4y_b4n"
    key_bytes = key.encode("utf-8")

    # Convert hex to bytes
    encrypted_bytes = bytes.fromhex(hex_data)

    decrypted_bytes = bytearray(len(encrypted_bytes))
    key_len = len(key_bytes)

    # Perform XOR to decrypt
    for i, b in enumerate(encrypted_bytes):
        decrypted_bytes[i] = b ^ key_bytes[i % key_len]

    # Check for ZIP signature (PK..)
    if decrypted_bytes.startswith(b'\x50\x4B\x03\x04'):
        print("[+] Detected ZIP file header.")
        output_filename = "secret_result.zip"
    else:
        print("[!] Warning: Unknown file type.")
        output_filename = "secret_result.bin"

    # Write to file
    with open(output_filename, "wb") as f:
        f.write(decrypted_bytes)

    print(f"[+] Decrypted file saved as: {output_filename}")
    print("[+] Please unzip this file to see the contents.")


if __name__ == "__main__":
    solve_puzzle()
```

Chạy code này ta thu được 1 file zip, bên trong có 1 file txt. Nếu chỉ nhìn phần đầu, ta thấy nó là một link Youtube (nhưng mà là Dích Dôn).

Nếu kéo xuống, ta xe thấy:

<img width="1432" height="88" alt="image" src="https://github.com/user-attachments/assets/9118f81a-923c-420c-8467-af2b7e27172b" />

Quay trở lại Github, nếu ta thêm .patch vào sau đuôi commit, ta có thể thu được email của người commit. Trong trường hợp này:

<img width="1919" height="1008" alt="image" src="https://github.com/user-attachments/assets/f3c48210-c065-4f8c-a16a-88327936e0bc" />

Tìm email này trên tiktok ta ra được 

<img width="1919" height="971" alt="image" src="https://github.com/user-attachments/assets/75c63e8d-245a-43be-8a12-527ca859ce55" />

Vào kênh ta có

<img width="1519" height="964" alt="image" src="https://github.com/user-attachments/assets/1f32d734-9c21-45d8-acce-e3d18b366225" />

Cái clip thực ra không có tác dụng gì trong việc tìm flag

_kh0n6_c0_ny

## Part 5: Google Maps và cái kết của bài toán

Ở anh trước, ngoài part 4 ra, ta thấy chủ tài khoản này sống ở Thành Phố Hồ Chí Minh

Tìm cơ sở KMA ở miền Nam, lại là phần đánh giá, ta sẽ thấy:

<img width="394" height="585" alt="image" src="https://github.com/user-attachments/assets/fd947790-1c31-4392-a644-4e00e64672d5" />

Khi nhìn vào cụm "Myxqbkd! drsc gsvv lo dro vkcd zkbd yp dro pvkq", lùi mỗi chữ cái đi 10 bước (Caesar Cipher), ta thu được:

"Congrat! This will be the last part of the flag"

Khả năng là mỗi chữ cái trong đoạn ở dưới cũng sẽ cần được lùi 10 bước, ta thu được một link Google Drive

<img width="1919" height="1037" alt="image" src="https://github.com/user-attachments/assets/5e3ae8b3-a968-4c19-9a4a-3398e8b5c1a4" />

Tải 2 bước ảnh về và làm đúng như sau:

https://github.com/user-attachments/assets/d5f19352-ba64-42e8-8d46-812e14086e8f

Hình ảnh thu về có một phần như sau:

<img width="324" height="109" alt="image" src="https://github.com/user-attachments/assets/7cf2971d-f68a-479f-b6da-9c2d2da69e72" />

Nếu chịu khó nhìn kĩ, hoặc dùng công cụ XOR của phần mềm Paint.net, ta thu được dòng chữ:

d1_ch01_n031_:3}

## Finale

Ghép tất cả lại, ta có flag: KCSC{cHuC_C4c_b4n_614n6_51nh_Vu1_v3_l3u_l3U_m4y_b4n_kh0n6_c0_ny_d1_ch01_n031_:3}

Chúc mọi người một giáng sinh vui vẻ. Và đúng vậy, tôi là người không có ny đây :-)))
