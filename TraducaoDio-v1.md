pip install googletrans

from flask import Flask, request, jsonify
from googletrans import Translator

app = Flask(__name__)

@app.route('/traduzir', methods=['POST'])
def traduzir_texto():
    data = request.get_json()
    texto_original = data['texto']

    translator = Translator()
    resultado = translator.translate(texto_original, src='en', dest='pt')
    traducao = resultado.text

    return jsonify({'traducao': traducao})

if __name__ == '__main__':
    app.run(debug=True)
    
