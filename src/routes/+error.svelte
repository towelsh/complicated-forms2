<script lang="ts">
    import { page } from "$app/stores";
    let heading = $page.error?.message;
    let msg = "An unexpected error occurred.";
    switch ($page.error?.message) {
        case "FormNotFound":
            heading = "Form not found";
            msg = "The form you're looking for was not found. It may have been deleted.";
            break;
        case "FormClosed":
            heading = "Form closed";
            msg = "This form is currently not accepting new submissions.";
            break;
        case "FormExpired":
            heading = "Form expired";
            msg = "This form is no longer accepting new submissions.";
            break;
        case "FormAuthRequired": 
            heading = "Form is restricted";
            msg = "You are not authorized to access this form. Please contact the owner to request access.";
            break;
        case "FormAuthInvalid":
            heading = "Invalid access link";
            msg = "Your access link is invalid. Please contact the owner to request a new link.";
            break;
        case "FormAuthExpired": 
            heading = "Access link expired";
            msg = "Your access link has expired. Please contact the owner to request a new link.";
            break;
        case "FormMalformed":
            heading = "Malformed form";
            msg = "The form you're looking for is not a valid form. It may have been deleted. Please contact the owner.";
            break;
    }
</script>

<div class="latte mx-auto w-4/6 m-5 p-8 bg-gradient-to-r from-surface0 to-crust rounded shadow-md">
    <div class="flex items-center">
        <span class="material-icons md-48 h-5 mr-4 mb-1 md-dark">error</span>
        <div>
            <h1 class="text-3xl font-bold"><span class="bg-blue-400 rounded p-1 text-xl leading-9 align-middle">{ $page.status }</span>
                {heading }</h1>
            <p class="text-gray-800">{msg}</p>
        </div>
    </div>
</div>