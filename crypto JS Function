import CryptoJS from "crypto-js";

export const encryptData = (data: string, SECRET_KEY: string) => {
    return CryptoJS.AES.encrypt(data, SECRET_KEY).toString();
};

export const decryptData = (cipherText: string, SECRET_KEY: string) => {
    const bytes = CryptoJS.AES.decrypt(cipherText, SECRET_KEY);
    return bytes.toString(CryptoJS.enc.Utf8);
};
