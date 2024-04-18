<script>
	import logo from './images/logo.png';
</script>

<header>
	<div class="sti">
		<a href=""><img class="logo" src={logo} alt="" /></a>
		<a href=""><div class="text">STI Education Services Group</div></a>
	</div>
	<nav>
		<a class="helpdesk" href="https://helpdesk.sti.edu/User/Login?ReturnUrl=%2f">Campus Helpdesk</a>

		<a class="faq" href="https://elms.sti.edu/page/show/495374">FAQ</a>
		<div class="log-in">Log in</div>
	</nav>
</header>

<style lang="scss">
	$primary-color: #0C3057;
$secondary-color: #3983d2;
$text-color-1: black;
$text-color-2: white;


a{
    text-decoration: none;
    color: inherit;

}

	header {
		z-index: 100;
		position: fixed;
		top: 0;
		display: flex;
		justify-content: space-between;
		align-items: center;

		width: 100%;
		color: $text-color-1;
		background-color: rgb(255, 255, 255);
		box-shadow: 1px 1px 25px -11px rgba(0, 0, 0, 0.75);
		border-top: $primary-color solid 4px;
	}

	.sti {
	
		:hover {
			.text {
				color: red;
			}
		}

		padding: 0 30px;
		display: flex;
		align-items: center;
		gap: 20px;

		.logo {
			width: 70px;
		}

		.text {
			font-size: 26px;
			padding: 0;
			color: black;
		}

		.text:hover {
			
		}
	}

	


	nav {
		padding: 0 40px;
		display: flex;
		align-items: center;
		color: $text-color-1;

		.faq,
		.helpdesk {
			cursor: pointer;
			padding: 24px 10px;
		}
		.log-in {
			cursor: pointer;
			background-color: $primary-color;
			color: $text-color-2;
			padding: 5px 12px 8px 12px;
			border-radius: 100px;
			transition: all 0.2s;
		}

		.log-in:hover {
			background-color: rgba($primary-color, 0.8);
		}

		.faq {
			margin-right: 10px;
		}

		.faq:hover,
		.helpdesk:hover {
			background-color: rgb(232, 232, 232);
		}
	}

	@media only screen and (max-width: 600px) {

	.sti {
		.text {
			display: none;
		}
	}
	
	
}
</style>
