from PIL import Image
import random
import os

def overwrite_image(image_path):
    try:
        with Image.open(image_path) as img:
            img_data = img.tobytes()
            img_size = len(img_data)
            mutable_data = bytearray(img_data)
            for i in range(0, img_size, 10):
                mutable_data[i] = (mutable_data[i] + random.randint(1, 255)) % 256
            img_modified = Image.frombytes(img.mode, img.size, bytes(mutable_data))
            img_modified.save(image_path)
        print(f"La imagen {image_path} ha sido sobrescrita y el contenido oculto ha sido eliminado.")
        return True
    except Exception as e:
        print(f"Ocurrió un error al sobrescribir la imagen: {e}")
        return False

if __name__ == "__main__":
    image_path = input("Ingrese la ruta de la imagen: ")
    if not os.path.isfile(image_path):
        print(f"La imagen {image_path} no existe.")
    else:
        success = overwrite_image(image_path)
        if success:
            print("El contenido oculto ha sido sobrescrito con éxito.")
        else:
            print("No se pudo sobrescribir la imagen.")
