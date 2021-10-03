# pass-data-child-to-parent



import React, {useState, useEffect} from "react";

function App() {

	const [formIsSubmit, setFormIsSubmit] = useState(false);
	
	const [name, setName] = useState('');

	const subMitForm = (value) => {
		setName(value);
		setFormIsSubmit(true);
	}

	return (
		<>
			<h1>Biểu mẫu
				{formIsSubmit ? ` ${name} đã được` : ' chưa được'} gửi
			</h1>
			<Children isSubmit = {subMitForm}/>
		</>
	);
};

const Children = ({isSubmit}) => {

	const submitForm = (e) => {
		e.preventDefault();
		console.log('đã được submit');
		isSubmit(name);
	};

	const [name, setName] = useState('');

	useEffect(()=>{
		if(name === '')
		{
			console.log('chưa nhập teen')
		}
		else {
			console.log('data đã đầy đủ')
		}
	});

	return (
		<>
			<form onSubmit = {submitForm}>
				<input onChange = {(e)=>setName(e.target.value)} name = "name"/>
				<p>Tên người đang nhập : {name}</p>
				<button type = {'submit'}>Gửi</button>
			</form>
		</>	
	)
}

export default App;
