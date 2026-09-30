from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

# A simple Pydantic model for data validation
class Item(BaseModel):
    name: str
    price: float
    is_offer: bool | None = None

# A basic GET endpoint
@app.get("/")
def read_root():
    return {"message": "Welcome to your FastAPI backend!"}

# A POST endpoint accepting a JSON request body
@app.post("/items/")
def create_item(item: Item):
    return {"item_name": item.name, "total_price": item.price * 1.1}
