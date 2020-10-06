import urllib.request, urllib.parse, urllib.error
import json
import ssl

api_key = False
# If you have a Google Places API key, enter it here
# api_key = 'AIzaSy___IDByT70'
# https://developers.google.com/maps/documentation/geocoding/intro

if api_key is False:
    api_key = 42
    serviceurl = 'http://py4e-data.dr-chuck.net/json?'
else :
    serviceurl = 'https://maps.googleapis.com/maps/api/geocode/json?'

# Ignore SSL certificate errors
ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

while True:
    address = input('Enter location: ')#enter in the place you are seraching for
    if len(address) < 1: break

    parms = dict()
    parms['address'] = address#this is the name of the place being searched
    if api_key is not False:
        parms['key'] = api_key#api_key is the key to access the api for the website
    url = serviceurl + urllib.parse.urlencode(parms)#parsing the parameters then adding it to the url to search for the specified place

    print('Retrieving', url)
    uh = urllib.request.urlopen(url, context=ctx)#opens the url
    data = uh.read().decode()#reads and decodes the url data
    print('Retrieved', len(data), 'characters')

    try:
        data_read = json.loads(data)#loads the json data into a dictionary, this is so we can search through and parse the json file
        place_id = data_read['results'][0]['place_id']#search through the json file for the place_id needed
        city_id = data_read['results'][0]['address_components'][2]["short_name"]
        print('Place_ID: ', place_id)
        print("City: ", city_id)
    except:
        print("Error!!!!!")

class PartyAnimal:
    x = 0
    name = ""

    def print_name(self, user_input):
        self.name = user_input
        print(self.name)

    def party(self):
        self.x = self.x + 1
        print("So far", self.x)
        print(self.x)


an = PartyAnimal()

an.party()
an.print_name("Logan")
an.party()
an.party()
print(PartyAnimal.x)
