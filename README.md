def create_readme(repo_name, access_token):
    headers = {
        'Authorization': f'token {access_token}',
        'Accept': 'application/vnd.github.v3+json'
    }

    readme_content = '''# Judul Repositori

Tulis deskripsi repositori di sini.

## Instalasi

Tulis langkah-langkah instalasi di sini.

## Penggunaan

Tulis petunjuk penggunaan di sini.

## Kontribusi

Terima kontribusi dari para pengembang.

## Lisensi

Tulis jenis lisensi di sini.'''

    data = {
        'message': 'Create README',
        'content': readme_content
    }

    response = requests.put(f'https://api.github.com/repos/{repo_name}/contents/README.md', headers=headers, data=json.dumps(data))

    if response.status_code == 201:
        print("README berhasil dibuat!")
    else:
        print(f"Terjadi kesalahan saat membuat README. Kode status: {response.status_code}")
        print(response.json())

# Ganti dengan access token GitHub pribadi Anda
access_token = 'access_token_anda'

# Ganti dengan nama repositori yang ingin Anda buat README
repo_name = 'nama_repositori'

create_readme(repo_name, access_token)
