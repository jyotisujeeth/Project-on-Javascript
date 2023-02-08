# Project-on-Javascript
his will be a simple project. Using the concepts that you have learnt in the previous assignment you can easily solve this
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body><form onsubmit="saveToLocalStorage(event)">
    <label for="Amount">Choose Expense Amount</label>
    <input type="number" name="Amount" id="AmountInput" >
    <label for="Description" >Choose Description</label>
    <input type="text" name="Description" id="DescriptionInput">
    <select name="Catagory" id="CatagoryInput">
        <option value="Movie">Movie</option>
        <option value="Travel">Travel</option>
        <option value="Dinner">Dinner</option>
        <option value="Diesel">Diesel</option>
        <option value="Shopping">Shopping</option>
        <option value="Grocery">Grocery</option>
    </select>
    <label for="submit"></label>
    <button>submit</button>
</form>
<u id="listofitem"></u>
<script>
 function saveToLocalStorage (event){
            event.preventDefault();
            const Amount=event.target.Amount.value;
            const Description=event.target.Description.value;
            const Catagory=event.target.Catagory.value;
          
            const obj = {
                Amount,
                Description,
                Catagory
            };
            localStorage.setItem(obj.Amount,JSON.stringify(obj));
            showUserOnScreen(obj)
        }
        function showUserOnScreen(obj){
            const parentElem =document.getElementById('listofitem');
          
            const chidElem =document.createElement('li');
            chidElem.textContent=obj.Amount+'-'+obj.Description+'-'+obj.Catagory

             const deleteButton=document.createElement('input');
             deleteButton.type="button"
             deleteButton.value='Delete'
             deleteButton.onclick=()=>{
                localStorage.removeItem(obj.Amount)
                parentElem.removeChild(chidElem)
             }
             
        const editButton=document.createElement('input');
             editButton.type="button"
             editButton.value='Edit'
             editButton.onclick=()=>{
                localStorage.removeItem(obj.Amount)
                parentElem.removeChild(chidElem)
                document.getElementById('AmountInput').value = obj.Amount
                document.getElementById('DescriptionInput').value = obj.Description
                document.getElementById('CatagoryInput').value = obj.Catagory
             }
             chidElem.appendChild(deleteButton)
             chidElem.appendChild(editButton)
             parentElem.appendChild(chidElem)
            }
            </script>
</body>
</html>
